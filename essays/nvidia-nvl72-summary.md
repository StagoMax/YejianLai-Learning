# NVIDIA NVL72 Summary

## Core hardware structure

The NVL72 system is built around NVLink 5 and NVSwitch 5.

At the highest level, one NVL72 rack contains:

- 72 Blackwell GPUs
- 36 Grace CPUs

Each logical Blackwell GPU is composed of two GPU dies.

A single GPU has 18 NVLink interfaces, and each interface runs at 100 Gb/s, which gives one GPU a total NVLink bandwidth of 1,800 Gb/s.

The rack itself is organized into:

- 18 compute trays
- 9 NVSwitch trays

Each compute tray contains four GPUs and two Grace CPUs.

Each NVSwitch tray contains two NVSwitch chips.

A single NVSwitch ASIC exposes 72 NVLink ports.

The link interfaces are connected through high-speed copper cables.

## How GPUs connect to NVSwitch trays

Each GPU has 18 link interfaces. Those 18 interfaces are distributed across 9 NVSwitch trays, with two links going to each tray.

That means one NVSwitch tray receives two links from every GPU in the rack. Since the rack has 72 GPUs, one NVSwitch tray must handle 72 x 2 = 144 interfaces in total, which is why it is implemented with two NVSwitch chips.

Each NVSwitch tray therefore provides 14.4 Tb/s of bandwidth.

## Data flow inside the rack

A single GPU has 1,800 Gb/s of total NVLink bandwidth. When GPU A sends data to GPU B, that data is split into 9 parts and sent through the 9 NVSwitch trays in parallel. The 9 trays then transmit those pieces to the destination GPU almost simultaneously.

This is what makes the internal rack communication so aggressive in bandwidth terms.

During All-Reduce, the NVSwitch fabric does more than just forward packets. It can also perform reduction in hardware through SHARP, so the reduction work happens while data is flowing through the switch fabric rather than requiring an extra software-side aggregation path.

In other words, when 72 GPUs need to sum their intermediate results and redistribute them, the reduction can be executed directly inside the NVSwitch path by hardwired logic, and then the results are sent back to the participating GPUs.

## SHARP

SHARP stands for Scalable Hierarchical Aggregation and Reduction Protocol.

Its importance is that it turns the network path itself into part of the computation path.

In a normal view of distributed training, All-Reduce sounds like "take the outputs from 72 GPUs, add them together, then distribute the result." With SHARP, the reduction is performed directly inside the NVSwitch path while the data is in flight.

That reduces the amount of back-and-forth data movement between GPUs and improves collective communication efficiency significantly.

## Cross-rack communication

Cross-rack communication is built on:

- InfiniBand
- ConnectX NICs
- QM9700 switches

One rack contains 72 ConnectX NICs.

Each compute tray contains four ConnectX NICs, corresponding to four GPUs, and also one DPU that offloads lower-level work such as data movement, network communication, storage encryption, and security handling.

Each ConnectX NIC provides 800 Gb/s single-port external throughput.

Rack-to-rack communication uses a fat-tree topology based on QM9700 switches.

## Leaf-Spine topology

At the first layer are the Leaf switches.

The 72 NICs in one rack fan out into 72 800G optical or active optical links. These 72 NICs are divided into 8 independent rails, and each rail contains 9 NICs.

A QM9700 switch has 64 ports, using a 32-downlink / 32-uplink non-blocking design. That means 32 ports connect downward to NICs and 32 ports connect upward to Spine switches.

Because one rack has 72 NICs, the downlink side needs at least 72 / 32 = 2.25 Leaf switches. In real deployments, multiple Leaf switches are pooled together, and rail-local access is used, so GPUs with the same relative position and rail number across different racks preferentially connect into the same Leaf group.

At the second layer are the Spine switches, which aggregate the uplinks from the Leaf layer.

## A simpler summary of the overall system

At the composition level:

- two GPU dies form one GPU chip
- two GPU chips plus one Grace CPU form a compute module
- two compute modules plus four ConnectX NIC modules and one DPU module form a compute tray
- two NVLink switch chips form one NVSwitch tray

At the rack level, one rack contains:

- 72 GPUs
- 18 compute trays
- 9 NVSwitch trays

At the connection level:

Each GPU has 18 links, and every two links are assigned to one NVSwitch tray. Each NVSwitch chip handles one of those links. This creates a fully parallel and symmetric transmission structure. Across the rack, every NVSwitch tray connects to every GPU.

At the data-flow level:

Data from GPU A is split into 9 parts, sent to the 9 NVSwitch trays, and then forwarded nearly simultaneously to GPU B. This is what gives the system its theoretical 1,800 Gb/s peer communication bandwidth per GPU.

When the workload is All-Reduce, the NVSwitch path can also sum the results from all 72 GPUs and redistribute them, using labels to identify and route the reduction path entirely in hardware.

## Cross-rack scaling

When communication crosses racks, data is split across the 72 ConnectX NICs and sent to the Leaf switches. Since each Leaf switch offers 32 downlinks and 32 uplinks in a non-blocking design, a rack needs at least 2.25 Leaf switches just to terminate the rack's 72 NICs.

Each uplink then connects upward into the Spine layer. At moderate scale, Spine can directly interconnect the Leaves. At larger scale, a Core layer is introduced above Spine.

A ConnectX NIC runs at 800 Gb/s, so a 64-port switch offers 51.2 Tb/s of switching bandwidth.

The important idea is that the ports are designed to be highly symmetric. Data is split across many transmission nodes, carried in parallel across the network fabric, and then reassembled at the destination. The architecture is designed to maximize bandwidth and minimize blocking.

## Rail design

The 72 NICs in one rack are divided into 8 rails, and each rail contains 9 NICs.

One rack's rail-0 therefore has 9 NICs. If there are 3 racks, there are 27 rail-0 NICs in total, and a Leaf switch can gather those rail-matched NICs together. In larger pooled deployments, the small-port waste is diluted as scale increases.

For example, at 32 racks:

- rail-0 NIC count = 32 x 9 = 288 NICs

At that point, the rail-based grouping becomes much more efficient.

## Scaling limits

In a two-layer Leaf-Spine fabric, if a Spine can connect to 64 Leaves, then in simple theoretical terms the fabric can support 64 x 32 = 2,048 GPUs.

With a Core layer above Spine, the system can scale further. NVIDIA's DGX B200 SuperPOD-style expansion can push the fabric to tens of thousands of GPUs.

At even larger scale, the common direction is multi-pod or multi-fabric expansion.

From NVIDIA's official GB200 NVL72 reference topology, one scale unit is split into four SLGs, each consisting of 8 Leaf switches and 6 Spine switches. In that reference design, a Spine does not simply talk to each Leaf through one port. Each Leaf generally occupies multiple 400G ports on the Spine in order to preserve the non-blocking fat-tree property.

## The role of Grace CPU

Grace CPU is not there to replace GPU matrix multiplication.

Instead, it acts more like the host CPU and large-memory hub inside each compute tray.

Each compute tray contains two Grace CPUs and four Blackwell GPUs. Grace is responsible for:

- running the operating system
- handling CUDA / NCCL / driver layers
- task scheduling
- data preprocessing
- I/O
- networking and storage stack work
- serial control logic that GPUs are not good at

Grace is tightly coupled to Blackwell through NVLink-C2C, which creates a shared coherent address space between CPU LPDDR5X memory and GPU HBM.

So this is not the traditional "CPU with a few attached GPUs" model. It is a deeply fused CPU/GPU supernode.

The fast All-Reduce data path still primarily lives in GPU + NVLink/NVSwitch + NIC + switch fabric. Grace is more responsible for orchestrating, feeding, scheduling, and managing memory and system behavior.

## The role of the DPU

The DPU is better understood as a network, storage, and security coprocessor.

It mainly handles north-south traffic, including:

- external storage access
- in-band management
- remote provisioning and elastic orchestration
- telemetry collection
- security isolation
- virtual switching
- storage acceleration

The true east-west training traffic still mainly flows through ConnectX.

Put simply:

- GPU does the computation
- Grace manages the host and memory
- DPU handles networking, storage, and security services

## CPU removal from the hot data path

During tensor exchange across NVLink and NVSwitch, Grace CPU does not sit in the middle of the fast path.

It does not relay data. It does not intervene in the communication path.

At the hardware level, this is enabled through GPUDirect P2P and direct memory access between GPU memory and the NVSwitch fabric.

That is why the latency is so low and why the CPU bottleneck is removed from the communication-critical path.

Grace CPU's real job is still on the orchestration side:

- run Linux
- tokenize input prompts
- schedule external storage to load model weights
- convert output tokens back into human-readable text

## Microscopic tensor-parallel data flow

If we look at the system from the perspective of tensor parallelism, the flow becomes easier to imagine.

Suppose TP = 72, meaning all 72 GPUs participate in tensor-parallel execution.

GPU 0 finishes one layer's matrix multiplication and produces a set of intermediate tensors. It now needs an All-Reduce or All-to-All communication step.

Its communication controller slices the data into 18 parts and sends those pieces out simultaneously across all 18 physical interfaces at a fully utilized 1,800 GB/s aggregate rate.

The 9 NVSwitch trays, acting like a non-blocking highway interchange, forward the pieces directly to the target GPUs with near-instant routing.

The key advantage is non-blocking communication. Whether two GPUs are talking or all 72 GPUs are communicating heavily at the same time, data still only needs one NVSwitch hop, with roughly 100 ns delay, while each GPU can continue to consume the full internal bandwidth.

## SHARP at the microscopic level

SHARP matters again at this microscopic communication level.

During All-Reduce, data streams tagged for reduction are combined inside the NVSwitch path itself. The switch identifies the label, applies the reduction operation directly in hardware, and returns the result to all participating GPUs.

This effectively turns the network into part of the compute path and reduces how many times data must be moved back and forth among GPUs.

That is why SHARP can dramatically improve communication efficiency in large-model clusters.

## Reference

https://developer.nvidia.com/blog/nvidia-nvlink-and-nvidia-nvswitch-supercharge-large-language-model-inference/?ncid=no-ncid

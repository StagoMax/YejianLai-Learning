# Career Choice

This piece explains my thinking about career choice in detail.

What follows are the directions I identified after research, but later in the piece I also explain which parts I would eliminate and why.

## Several directions I observed

### AI Infra / AI Infrastructure Engineering

Build distributed training platforms, work on resource scheduling and DevOps, and eventually become responsible for a company's AI infrastructure.

### Large-model data engineering

This includes data pipelines for training, evaluation, and applications:

- collection
- cleaning
- deduplication
- labeling
- quality control
- sample augmentation
- distribution governance

### Benchmark evaluation engineering

This is about designing task sets, evaluation sets, metric systems, red-team testing, regression cases, and comparison platforms.

The core is not "manual testing." The core is engineering the model quality system itself.

### Embodied-intelligence data engineer

This role handles data collection, cleaning, slicing, labeling, quality inspection, storage, versioning, replay, and training-data interfaces, so that algorithm teams can stably obtain high-quality data to train models.

### Embodied-intelligence simulation engineer

This role uses platforms such as Isaac Sim, Gazebo, MuJoCo, Unity, and Unreal to build simulation environments; imports robot URDF/SDF; tunes joints, collision, friction, and sensors; simulates RGB, depth, LiDAR, IMU, and other sensor signals; runs large-scale experiments; and supports Sim2Real transfer from simulation into real robots.

This is also exactly what many real robotics simulation roles already look like.

### Embodied-intelligence evaluation engineer

This role designs benchmarks, test tasks, scoring metrics, automated evaluation scripts, failure-case analysis, and test reports.

For example, evaluation roles around embodied VLA often require multidimensional and quantifiable benchmarks that cover perception, cognition, planning, control, and the full chain around them.

### High-performance computing engineer

This sits near the top of the AI engineering pyramid and mainly focuses on:

- squeezing performance from the chip layer
- optimizing cross-node communication such as NVLink-style mechanisms
- restructuring the lower layers of deep-learning frameworks

### Solutions engineer (FDE) or frontier deployment engineer

This role is the bridge between customers and R&D.

It translates customer needs into product requirements, provides demos that persuade customers, deploys systems on the customer side, and feeds problems and constraints back to the engineering side.

### Agent harness engineer

Agent = Model + Harness.

This direction is more about building the systems, tools, and bridges that connect AI to the real world. From a product perspective, it is very important.

## Three major directions

I think this can roughly be split into three large directions:

1. embodied intelligence
2. AI Infra
3. AI application

## About embodied intelligence

I have to say this clearly: I do not think embodied intelligence is a good short-term direction.

It is still very immature.

Even the best current models still do not have especially high success rates on real task execution. And the cost of failure in real-world robotics is very high. A small mistake can mean a broken cup, damaged objects, or worse.

To push even single-task success rates higher, several deep problems still need to be solved:

1. **Hardware problems**: maintenance, failures, flexibility, and reliability.
2. **Severe data shortage**: even learning from human video data still requires a model that already has a basic understanding of the world. Long-tail scenarios are enormous, and the data bottleneck is extreme.
3. **Gap problems**: there are huge gaps between simulation and the real world, as well as between different real robots. Transfer and generalization are still very hard.
4. **Vision alone is not enough**: many real situations require anticipation, intention recognition, touch, hearing, and even smell in some domains. Humans can close their eyes and still retrieve an object from a pocket or scratch an itch because the brain maintains spatial understanding. Current models do not have that.
5. **Safety**: the consequences of robot mistakes are too large.

Because of these issues, I do not think embodied intelligence will mature within three to five years. It may not even mature within ten.

So I do not think it is a good field to enter too early.

Embodied intelligence is also very different from LLMs. LLMs scale through the network. Robots do not. You need a large installed base of robots, but that installed base depends on the system already being useful in the real world. That creates a loop.

So even if embodied intelligence reaches its "GPT-3 moment," expansion may still be slow.

That is why I do not strongly recommend that people rush into embodied intelligence now, unless they are highly passionate and willing to make a long-term bet.

So I would eliminate directions tightly bound to embodied intelligence for now.

## About AI Infra

AI Infra has many sub-directions, and I think it should be decomposed from the bottom layer upward.

### Starting from chips

There are many chip categories:

- GPU
- NPU
- TPU
- LPU

Each is optimized around different purposes and model-layer demands. Above the chips are instruction sets and low-level execution models.

Then come parallel computing frameworks, such as:

- CUDA
- CANN

Then AI compilers and DSL layers, such as:

- Triton
- TVM
- XLA

Then distributed communication:

- InfiniBand
- RDMA
- NCCL
- HCCL

Then deep-learning frameworks:

- PyTorch
- TensorFlow / JAX
- MindSpore

Then inference and training acceleration:

- inference engines such as vLLM, SGLang, TensorRT
- operator fusion and quantization
- training acceleration such as DeepSpeed and Megatron-LM

Then resource scheduling, virtualization, and container orchestration:

- Kubernetes
- Docker
- MIG
- vGPU

Above that layer, things become more similar to traditional backend and application engineering.

### One direction I think should be avoided

I do not think it is a good idea to move into generic AI application engineering that is unrelated to GPU-heavy infrastructure, such as broad "AI integration into enterprises" roles.

The reason is simple: competition there explodes very quickly. It attracts a large number of people switching over from other software backgrounds, and the competition level starts to resemble frontend or Java backend.

By contrast, backend engineers transitioning into AI Infra seems much more reasonable, and I think it is a stronger long-term direction.

## Roles at different layers

### Operator / high-performance computing (HPC)

Keywords:

- GPU / NPU / LPU architecture
- assembly and instruction sets
- CUDA
- CANN

Core responsibility:

Develop and optimize deep-learning operators for specific hardware architectures, such as matrix multiplication and convolution, often by writing low-level kernels directly and solving raw compute bottlenecks.

### AI compiler R&D

Keywords:

- Triton
- TVM
- XLA
- MLIR
- LLVM

Core responsibility:

Perform graph-level optimization, such as operator fusion and memory optimization, low-level code generation, and connecting graph compilers to different hardware backends.

### Large-model training / distributed systems

Keywords:

- InfiniBand
- RDMA
- NCCL / HCCL
- DeepSpeed
- Megatron-LM
- PyTorch / JAX

Core responsibility:

Design and optimize distributed training strategies such as data parallelism, tensor parallelism, and pipeline parallelism; solve multi-node communication bottlenecks; optimize checkpoint I/O; and maintain long-duration training stability and fault tolerance.

### AI deployment and inference acceleration

Keywords:

- vLLM
- SGLang
- TensorRT
- ONNX Runtime
- operator fusion
- KV cache optimization
- model quantization (FP8 / INT8 / INT4)

Core responsibility:

Push inference performance to the limit for business scenarios, reducing token latency and increasing throughput.

### AI platform / cloud-native scheduling engineer

Keywords:

- Kubernetes
- Docker
- MIG
- vGPU
- Golang
- traditional microservice architecture

Core responsibility:

Manage hundreds or thousands of GPUs, implement GPU isolation, pooling, elastic scaling, task scheduling, and backend interfaces for AI training platforms.

## A realistic constraint

These layers are not isolated. In practice, movement upward and downward across them is possible.

But I also spoke with several people already working in AI Infra, and they all emphasized the same thing: the field is highly degree-sensitive.

Without strong academic credentials, a person may need to make core contributions to a well-known open-source project, and that is often not something that can be done quickly. The difficulty of entering a major company is also higher.

## My practical conclusion

So my current conclusion is that the more pragmatic choices are:

- solutions engineer (FDE) or frontier deployment engineer
- agent harness engineer

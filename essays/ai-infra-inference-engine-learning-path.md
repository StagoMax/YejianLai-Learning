# AI Infra Inference Engine Learning Path

## A few practical things first

- projects
- contributions to open-source projects
- my own projects, which must be practical and directly relevant
- competitions, though I currently feel their priority is not very high

Write blogs and tutorials, both in Chinese and in English. Build a community, but focus on connecting with people who are truly in the industry rather than people who are still only learning. I need to connect with strong people, not beginners. Beginners are a burden unless they pay to learn. Strong people are what actually help a career.

Professional certificates depend on the situation. Sometimes there is no certificate that really matches the direction.

I must pay close attention to the frontier and to changes in the industry.

I also must make much better use of AI to amplify my own productivity.

## Two categories of inference-side optimization

Optimization on the inference side can be divided into two broad categories.

The first category is optimization that does not fundamentally change the model algorithm.

In simpler terms, this kind of optimization improves performance without changing the model architecture itself.

For example:

- low-level memory management: PagedAttention and Chunked Prefill, which balance compute between Prefill and Decode stages
- operator-level optimization: writing more efficient CUDA kernels, such as FlashAttention-2/3 and Triton-based operator fusion
- service-level scheduling: Continuous Batching, where requests are added immediately and removed as soon as generation ends instead of waiting for a full batch to finish
- lossless memory compression: basic KV-cache quantization, usually combined with simple scale factors and not requiring retraining

## The second category: algorithm-system co-optimization

The second category requires architecture changes and therefore retraining or fine-tuning.

This type of optimization can often bring order-of-magnitude gains, but it belongs much more to the category of algorithm research and usually requires cooperation with an algorithm team.

Examples include:

- changing the KV mechanism: replacing MHA with GQA to greatly reduce KV-cache size, or moving toward ideas such as MLA, where KV is compressed into a latent representation and the inference engine needs specialized operators
- abandoning global KV cache: using Sliding Window Attention, where the model only looks at the most recent N tokens and KV-cache length becomes fixed
- abandoning the Transformer architecture entirely: moving toward State Space Models such as Mamba or RWKV, where there is no KV cache that grows with sequence length, only a fixed-size hidden state

## If I want to enter this field now

If I want to enter this field from the current state, I probably have to bet on a future direction. Otherwise, ordinary work that looks the same as everyone else's gives no real advantage.

## Possible future directions

### Multi-agent systems

Long-horizon tasks and workflows that do not require human supervision are one likely direction.

The memory solution is a major unresolved problem.

To simplify the idea, I can use a water-pipe metaphor:

- intelligence output is the water
- the size of the pipe is the area of intelligence
- the speed of the water is the speed of intelligence output
- the water also cannot stop, meaning intelligence must remain stable over time

The future problems are all extensions of these constraints.

### The biggest current problem

The biggest current problem is not just output speed. It is stable and continuous intelligent output.

How do we form an effective loop of ongoing intelligence output without collapse?

Only after solving that should optimization of speed and scale really become the next step.

## What causes this problem now?

### 1. Exponential amplification of errors

Once an error happens, the direction has already drifted. If the system does not correct itself in time, the error gets amplified indefinitely.

### 2. Long context easily creates hallucination

With very long context, the model easily drifts from the goal, gradually forgets what it was trying to achieve, and falls into cycles of bug fixing and endless optimization.

Traditional RAG also lacks real understanding of temporal logic and causality, and abstract goals are often not represented clearly enough.

### 3. Feedback and validation loops

The model needs the right tools so that it can gain perception of the world, validate what happened, obtain feedback, and push itself forward step by step toward the goal.

## What follows from that?

If these problems are to be solved, then architecture itself has to change.

No amount of optimization on top of the traditional Transformer seems likely to solve this problem at the root.

But training a new architecture is very expensive.

And I do not have top-tier credentials. Even if I invented a new architecture, I might only end up rebuilding a team from scratch, while larger companies already have complete resources and could easily absorb the advantage.

One possible path would be to hand the architecture to a major company in exchange for reputation and some upside. But is that really worth it?

Without top-level compute clusters, even training a small model takes many times longer than it would inside a major company.

At the same time, I currently do not have enough capital and cannot easily raise funding.

So the pragmatic strategy is still to first get into a relevant company, and then see whether I can apply for compute resources to run experiments from the inside.

## How should I learn?

I do not think I should learn by following a traditional slow and systematic path.

AI tools are already powerful. If I insist on fully systematic study first, I may slow down my ability to produce actual results and real practice.

That said, a rough understanding is still necessary.

### 1. Understand frontier model principles

It is necessary to understand the principles of frontier models so that I can design inference engines more effectively.

Ideally, I should directly write my own summary of them.

### 2. Draw an AI Infra chain

I should draw an AI Infra chain, get a rough passing-level understanding of all the major parts, and then go deep into one direction rather than trying to master everything at once.

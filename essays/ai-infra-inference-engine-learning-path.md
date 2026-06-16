# AI Infra Inference Engine Learning Path

## Practical foundations

If I want to move seriously into AI Infra and inference engines, I cannot rely on vague interest alone. I need real projects, contributions to open-source projects, and my own work that is both practical and directly relevant. Competitions exist, but for now I do not think they should be the top priority.

I also need to write blogs and tutorials in both Chinese and English, and I need to build a real network. But the key is not simply "building a community." I need to connect with people who are actually in the industry, especially strong practitioners, rather than surrounding myself only with beginners. Beginners may want to learn, but they do not help career development unless there is a clear exchange of value. Strong people, on the other hand, shape trajectory.

Certificates only matter when there are actually useful certificates for the direction. In some cases there are none that truly match the work. What matters more is staying close to frontier developments, tracking where the industry is moving, and using AI aggressively to amplify personal productivity.

## Two kinds of inference optimization

On the inference side, optimization can roughly be divided into two categories.

The first category is optimization that does not fundamentally change the model algorithm. In other words, it improves performance without requiring the model architecture itself to be redesigned.

This includes things like low-level memory management, such as PagedAttention and Chunked Prefill, which help balance compute between the Prefill and Decode stages. It also includes operator-level optimization, such as writing more efficient CUDA kernels or using FlashAttention and Triton-based fusion. At the service layer, there are scheduling optimizations like Continuous Batching, where requests are admitted and removed dynamically rather than waiting for a full batch to finish. There is also relatively lightweight memory compression, such as basic KV-cache quantization that usually does not require retraining.

The second category is algorithm-system co-optimization. This category is much more powerful, but it also requires architectural changes and therefore retraining or fine-tuning. It usually belongs less to ordinary engineering optimization and more to actual algorithm research.

Examples include replacing MHA with GQA to reduce KV-cache size, moving toward architectures such as MLA that compress KV into latent representations and require specialized operators, adopting Sliding Window Attention so cache length remains fixed, or going further and leaving the Transformer family entirely for architectures such as Mamba or RWKV, which do not rely on sequence-length-growing KV caches at all.

This second category is where truly dramatic gains may happen, but it also demands much deeper coordination with algorithm teams.

## If I want to enter this field now

If I want to enter this field from my current position, I probably need to bet on a future direction rather than simply doing ordinary work with no clear strategic edge. Average-looking effort is unlikely to produce any real advantage in this area.

One obvious future direction is multi-agent systems, especially long-horizon tasks and workflows that no longer require direct human supervision. But the memory problem is still unresolved.

The easiest way to describe the challenge is to compare it to a water system. Intelligence output is the water. The width of the pipe is the scale of intelligence. The speed of the flow is the speed of intelligent output. And the flow cannot stop. That means the future of the field is not only about making the output stronger or faster. It is about making it stable enough to continue without collapse.

That is why I think the biggest problem today is not simply output speed. It is the problem of stable, continuous, reliable intelligent output. Only after that is solved does it make sense to optimize speed and scale more aggressively.

## Why stable long-horizon output is still so hard

There are several reasons this remains difficult.

First, errors amplify exponentially. Once the system begins drifting in the wrong direction, the mistake grows larger and larger unless it is corrected early enough.

Second, long-context behavior is still fragile. With enough context, models begin to hallucinate more easily, drift away from their actual goal, and sometimes fall into loops of endless bug-fixing or pointless optimization. Traditional RAG also does not truly solve the problem because it still lacks strong understanding of temporal logic, causality, and abstract long-term intent.

Third, models still lack robust feedback and validation loops. A model needs the right tools to perceive the world, verify whether what it did was correct, and obtain feedback that can guide the next step. Without that loop, it is very hard to sustain meaningful long-range progress.

Once you view the problem this way, it becomes hard to believe that traditional Transformer optimization alone will solve it at the root. That does not mean the current architecture is useless. It means there may be a ceiling on what these optimizations can fundamentally achieve.

## The architecture dilemma

If the root problem really does require architectural change, then another dilemma appears immediately.

Training a new architecture is extremely expensive. And I do not have elite credentials or top-tier institutional support. Even if I came up with something genuinely new, the likely outcome might simply be rebuilding a team from scratch while larger organizations with stronger resources absorb the advantage.

One possible path would be to hand a new architecture to a major company in exchange for reputation, attribution, and financial upside. But is that really worth it?

Without top-level compute clusters, even small-model experimentation takes far longer than it would inside a major lab. At the same time, I do not currently have enough capital, and fundraising is not realistic in the short term.

That is why the most pragmatic path still seems to be entering a relevant company first, then finding ways to gain access to compute resources and experimental space from within.

## How I should learn

I also do not think I should follow a traditional slow and fully systematic study path.

AI tools are already strong enough that if I insist on perfect systematic learning before building anything, I may only slow down my ability to produce real work and practical results. Still, I do need a broad enough understanding to avoid being blind.

There are two things that feel especially important.

First, I need to understand the principles behind frontier models. Without that, it is hard to design inference engines intelligently. Ideally, I should not just read papers passively. I should write my own summaries and build my own understanding.

Second, I need to map the entire AI Infra chain. I do not need mastery of every component right away. What I need first is a rough but coherent understanding of all the major parts, enough to become competent across the whole chain and then choose one direction to go deep on.

That seems much more realistic than pretending I can learn everything at once.

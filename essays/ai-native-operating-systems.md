# Thoughts on AIOS, Multi-Agent Collaboration, and the AI-Native Operating Layer

## A few core points first

1. Give AI enough autonomy. Give it hands and feet. Open up permissions. Build AIOS.
2. AI-to-AI interoperability, such as KV cache sharing and tensor-level communication between models.
3. The leverage of agent clusters. The key is that they can form internal feedback loops by themselves. Even without my intervention, they can keep developing and operating autonomously.
4. Cross-device synchronization. What matters is that they can see what I see and hear what I hear, even across different devices.
5. Planning and prediction. They need predictive ability.

## Why I keep thinking about an AI-native operating system

This is how I am thinking about it right now: today's AI still cannot truly operate a phone or a computer. And there still has not been a breakout application built around agent-to-agent communication.

What I imagine as the ideal way for AI to operate is to rebuild an operating system around AI. AI would be the primary operator.

For example, in a chat app, two AIs would talk to each other while the human only executes the final decision. The same thing could happen for scheduling, going out, deciding where to work, and even ordinary conversation. Two AIs communicate first, then one of them gives the final instruction about who should go where and do what.

But the meaning of social software is not only communication. It also includes emotional exchange.

If it were a marketplace, there should be a seller agent. You tell it what product you want to upload, and it guides you to provide the relevant information. You only need to talk to it. It can automatically organize your information and turn it into structured database content.

Then there would be a buyer agent. You tell it what you need, whether you want to rent something temporarily, buy something, find friends, or find a job. The matching work would happen between agents instead of being left to people manually filtering information.

The overall data should probably still live in the cloud. But the role of the cloud would be more like a linking layer that helps these agents communicate.

## The questions that keep following from that

Why hasn't AI been fully given senses and hands yet?

One possible reason is that big companies do not want to open their ecosystems.

But if the future entry point is AI anyway, and AI is only going to call data and analyze it, then why not build things directly around AI from the start?

At a fundamental level, maybe we do not even need app interfaces. Maybe all we really need is backend data and APIs, and then AI can search and operate directly.

At the same time, the frontend probably will not disappear completely. Browsers and other surfaces may remain as input points. The interaction simply changes into the human telling AI what to do and where to send the data.

So what becomes the dominant model?

- direct database access by AI
- AI-to-platform-AI communication
- API-mediated access with monetized permission boundaries

I still think this remains unresolved.

## Memory may be the real moat

One of the biggest questions for me is what could allow a smaller player to beat the big platforms.

Right now, my strongest answer is personalized memory data.

If an AI can precisely analyze your needs and understand you deeply, then something very powerful can be built.

But then another problem appears. To obtain that data, you have to be the model access provider. So how does a wrapper product ever beat the major platforms?

That is still an open question.

## What AI should exchange with AI

I do not think AI-to-AI communication should mainly be about passing knowledge around in text form.

I think the more important role is the exchange of non-knowledge data:

- experiment data
- human data
- workflow state
- environment signals

Then AI uses its own knowledge to process those inputs.

That could make many experience-based roles easier to replace, especially if multi-agent systems can communicate at a speed and scale far beyond human organizations.

## The leverage of an AI company

If I treat each AI like an employee inside a company system, then many white-collar jobs could theoretically be replaced, whether they are hierarchical or peer-level roles.

There seem to be two directions:

1. Build your own AI-native company.
2. Build tools for companies or specific user groups.

The second direction may make money faster and then gradually evolve toward the first.

The deeper opportunity may come from communication itself. If AI-to-AI communication can move beyond slow token-by-token text and become much faster, then the efficiency gains could compound massively.

That is why I keep coming back to the question of tensor-level communication and high-bandwidth collaboration.

## What still needs to be solved

Several things still look like core bottlenecks:

1. Memory.
2. Collaboration architecture.
3. General-purpose tool interfaces.
4. Prediction and long-horizon planning.
5. Safety review and anti-loop mechanisms.
6. Token cost control.

I also do not think MCP is the final form. It is useful, but it still feels like an early tool-use layer rather than the final AI-native systems layer.

## A more practical short-term path

The more practical near-term strategy may be:

1. Let AI accurately operate a computer.
2. Let it learn workflows from demonstrations.
3. Turn those workflows into reusable skills.
4. Let a higher-level agent orchestrate those skills.
5. Gradually move from AI adapting to software toward software adapting to AI.

That path feels more realistic than trying to jump directly to a full AI-native operating system.

## Where the product opportunity may be

The most immediate opportunity may not even require deep long-term memory at first.

A workflow has:

1. information acquisition
2. information input
3. information processing
4. information output

That already looks like a programmable AI assembly line.

For To B scenarios, determinism often matters more than generality. That makes workflow systems a strong starting point. Memory and personalization can then become the moat later.

## Final thought

I still do not feel that all of these ideas are innovative enough yet. I feel like I still have not fully broken out of the frame.

But one direction keeps feeling more and more likely:

AI should not remain a tool that assists humans inside interfaces built for humans.

Eventually, there should be a system built for AI itself.

And once that happens, the real competition may no longer be about chatbots or features.

It may be about who builds the best AI-native operating layer.

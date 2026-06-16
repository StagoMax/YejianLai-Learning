# 260313-ai Thinking

## A few core points first

1. Give AI enough autonomy. Give it hands and feet. Open up permissions. Build AIOS.
2. AI-to-AI interoperability, such as KV cache sharing and tensor-level communication between models.
3. The leverage of agent clusters. The key is that they can form internal feedback loops by themselves. Even without my intervention, they can keep developing and operating autonomously.
4. Cross-device synchronization. What matters is that they can see what I see and hear what I hear, even across different devices.
5. Planning and prediction. They need predictive ability.

## Debate section

### idea

This is how I am thinking about it right now: today's AI still cannot truly operate a phone or a computer. And there still has not been a breakout application built around agent-to-agent communication.

What I imagine as the ideal way for AI to operate is to rebuild an operating system around AI. AI would be the primary operator.

For example, in a chat app, two AIs would talk to each other while the human only executes the final decision. The same thing could happen for scheduling, going out, deciding where to work, and even ordinary conversation. Two AIs communicate first, then one of them gives the final instruction about who should go where and do what.

But the meaning of social software is not only communication. It also includes emotional exchange.

If it were a marketplace, there should be a seller agent. You tell it what product you want to upload, and it guides you to provide the relevant information. You only need to talk to it. It can automatically organize your information and turn it into structured database content.

And this could apply to almost anything personal: second-hand goods, rentals, apartments, friends, hiring, and more. In other words, nearly all of a person's personalized supply and demand could exist inside their own system. Everyone would have a dedicated agent that understands their needs extremely well.

Then there would be a buyer agent. You tell it what you need, whether you want to rent something temporarily, buy something, find friends, or find a job. The matching work would happen between agents instead of being left to people manually filtering information.

The overall data should probably still live in the cloud. But the role of the cloud would be more like a linking layer that helps these agents communicate.

### Keep asking further

My question is: why hasn't AI been fully given senses and hands yet?

One possible reason is that big companies do not want to open their ecosystems.

But if the future entry point is AI anyway, and AI is only going to call data and analyze it, then why not build things directly around AI from the start?

At a fundamental level, maybe we do not even need app interfaces. Maybe all we really need is backend data and APIs, and then AI can search and operate directly.

That said, the frontend probably will not disappear completely. Browsers, for example, still serve as an input surface where people upload knowledge. At that point, data on the internet becomes training data for AI. So then another question appears: why not let AI upload data directly based on user intent? Even then, there still has to be an input entry point. The interaction simply changes into the human telling AI what to do and where to send the data.

There are also many different personalized platforms on the internet. AI would likely choose among them and then connect to their databases or interfaces. There will also probably need to be some kind of judge in the middle, and that judge is likely AI too.

So what is the right communication model?

Should AI directly access platform databases? Or should user-side AI communicate with platform-side AI? Direct database access sounds more efficient.

Then another question follows: could there ever be one unified database that contains all information from all platforms, just divided into different branches or trees that can be searched?

That sounds unlikely.

It may be easier in practice for platforms to encrypt their data as their own tree-like structure and monetize access through APIs.

So maybe the frontend really will fade away, or at least shift toward the AI entry point, where AI dynamically renders the needed information.

Would that create even more monopoly power, since there would be less room for new products to compete through traditional distribution?

Probably the AI entry point would still carry ads, so monetization could still happen there.

But then the harder question is: what would allow someone to build an AI entry point that surpasses the big companies? What actually makes users stay? What makes them not want to leave?

My current answer is personalized memory data.

If an AI can precisely analyze your needs and understand you deeply, then something very powerful can be built.

But then another problem appears. To obtain that data, you have to be the model access provider. So how does a wrapper product ever beat the major platforms?

There must be something more innovative than that, something that combines with other properties. But what is that missing property?

And what is MCP really? Is it an AI-to-AI protocol? Or an AI-to-platform-data protocol?

I do not think it is really either one.

Right now, MCP seems more like a way for AI to control tools, such as a CLI. True direct access to platform databases would probably not be allowed, except in limited forms through selected APIs.

But if AI calls those APIs, does that count as accessing the database?

At the end of the day, it is still searching, retrieving structured values, and sending them back to the model.

### A further version of the vision

I want to know whether, in the kind of future I am imagining, data from different functions and platforms would still remain separate.

Could one person eventually have one integrated set of information covering all of their functions and needs, and then whichever agent is activated would automatically know which parts of that information to use?

### Another thought

I also keep thinking about this:

In the past, when I hit a programming bug, I went to a browser to search for the solution. Now I directly ask an AI agent to solve it.

That shift did not happen because AI is better at searching the browser. It happened because AI already contains the knowledge needed to solve that kind of bug and can directly modify the code.

It is not solving the problem by asking another AI that knows the answer.

In the current interaction model, I have become the assistant and supervisor. I mostly just give feedback.

If another AI with eyes and a brain could also take over the supervision and feedback work, then I would only need to describe what I want.

Take video editing as an example. In the future, AI probably will not watch the entire video carefully and then decide how to cut it step by step.

Instead, you would first describe the effect you want, discuss the plan with AI, confirm the plan, and then hand the raw pixel data to AI. It would generate the final video directly.

I do not think the future should look like one specialized AI asking another specialized AI for knowledge and then returning to solve the task.

I think it should move toward one general and unified intelligence that solves the knowledge part itself.

AI-to-AI communication on the internet should mainly be for non-knowledge data, such as experiment data or human behavioral data. Knowledge itself may converge toward a more unified and general model.

### What exactly should AI exchange with AI?

AI-to-AI communication will probably focus on non-knowledge data, such as experiment data or human data, and then AI will use its own built-in knowledge to process those inputs.

That would make many experience-based jobs easier to replace.

And the real leverage may come from building a multi-AI system that communicates extremely fast and can expand across many links. If its processing speed is higher than everyone else's, then it can make money.

Finance seems like one possible application area.

But would it beat quantitative systems? Or should it avoid competing with quant directly and instead differentiate through longer-horizon forecasts, short-term trend prediction, or some other niche?

If I treat each AI like an employee inside a company system, then many white-collar jobs could theoretically be replaced, whether they are hierarchical or peer-level roles.

And there seem to be two directions:

1. Build your own AI-native company.
2. Build tools for companies or specific user groups.

The second direction might make money faster, and then gradually evolve toward the first.

Tensor-level instant communication sounds attractive, but the bandwidth has to be high enough. If transmission is too slow, it may not actually outperform text output.

Unless the data can be compressed and decompressed in a highly efficient way, with faster access across modules. Inside the same module, maybe something like NVLink points toward what is possible.

But where would this kind of ultra-fast communication actually matter?

The answer may be simple: inside an AI company.

If a company can hire countless AIs and let them communicate with efficiency far beyond humans, then their total efficiency would jump dramatically, and the advantage would compound like a snowball.

So if I could build tensor-level communication between AIs and then use that to form an entire AI company, the coordination efficiency could far exceed human organizations.

Then the real question becomes: by how many times?

## What I still feel is not innovative enough

I still feel these ideas are not innovative enough. I have not fully broken out of the frame yet.

Right now, the rough directions in my head are:

1. Use AI as leverage, for example by running dozens of AIs at once and letting a main AI supervise and give feedback, reducing my own involvement.
2. Think beyond quantity. Can AI-to-AI communication move beyond one-token-at-a-time text output? Can two neural systems talk in a more direct and instantaneous way?
3. If I am the boss and AIs are the employees, what methods can I use to scale faster and make money faster?

## Some further extensions

### Memory

Human memory looks a lot like an enhanced neural network.

If memory is implemented through a small memory network plus matrix operations, like a dynamic adapter or personalized LoRA, then two problems appear:

1. Stacking it may reduce model intelligence.
2. Memory costs may explode.

### If we pursue efficiency to the extreme

What would a society look like if we pursued efficiency to the extreme and tried to remove as much human physical and cognitive labor as possible?

To replace physical labor, AI must control machines. Autonomous driving is one path. Embodied intelligence is another.

Because the range of scenarios is so broad, one single model will probably not dominate all products. Different models will split off to fit different scenarios.

And then we may realize that only scenarios requiring intelligence need intelligent machines. Machines may divide into two categories:

1. Machines with intelligence.
2. Tools controlled by intelligence.

Driving requires intelligence. Turning a light on and off does not. But then we need an interface that allows AI to control tools. That is where a new operating system would emerge.

### The problems that still need to be solved

1. Memory. A robot without memory cannot serve humans well.
2. AI collaboration. The most efficient system will be adaptive, role-based, and robust.
3. General-purpose tool interfaces. I do not think MCP is the final form.
4. AI also needs better tools, and eventually AI may need to design tools for itself.

### Looking through the lens of industrial revolutions

If we look back:

- First revolution: steam power plus mechanical carriers
- Second: electricity plus electrical carriers
- Third: information plus information-processing carriers
- Fourth: intelligence plus carriers that consume intelligence

And usually the carrier layer becomes more valuable.

The real value of intelligence is definitely not this current question-and-answer chat box format. That is far too limiting.

If intelligence can be distributed like electricity, then what you build is not just a chatbot. You build a machine that continuously consumes intelligence.

## The most ideal direction

The most ideal direction is minimal human intervention, or no intervention at all. Humans only issue commands and do not participate in execution.

To achieve that, long-term memory, selective memory loading, unloading, and avoiding memory overuse all become hard technical problems.

Memory should be loadable, unloadable, and perhaps even pluggable.

That is why I keep thinking there will eventually be an operating system made of AI.

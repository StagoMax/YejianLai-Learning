# Architecture and Functional Design

In the early stage, the direction has to be narrow enough, but it also has to point toward a much larger goal. That is the only way to generate cash flow. For an individual developer, building a general platform from the start is basically unwinnable. A detour is necessary.

The product must be guided by extreme user experience.

The speed of distribution also has to be fast enough. A self-reinforcing ecosystem has to be built.

## Thinking

What kind of product do I want to build, and what principles should define it?

If I want to build a platform-level product, turn my product into a platform, let developers build on top of it, and make it easier for users to use products, then is it a good idea to package workflows as products that can be bought and sold?

First, we need to understand what users actually want.

What users want is not to choose among workflows. What they want is to describe a need to my product, and for my product to automatically construct the workflow product that solves that need perfectly.

So users should never be forced to decide which workflow to use. That only increases cognitive burden. The best path is for AI to construct and select the optimal workflow.

In the early stage, AI should use my system's tools to build workflows, while users modify those workflows through natural-language feedback until they reach a usable state. At that point, the workflow becomes an asset, and it also creates user lock-in.

Then my product should capture workflow-construction data in order to optimize my AI. Over time, the AI would learn how to directly construct better workflows in one step.

That means there has to be a data-layer policy:

- which users' data can be used for training
- which users' data cannot

Free-trial data can be used. Paid-user data probably cannot.

But if the product is built for To B customers, users will not want their data used for training at all. At the same time, paid-user workflows may be even more valuable. So some level of anonymization may be necessary, for example only capturing workflow structure rather than private business data.

If I turn this into a platform, what is the benefit? Should users be allowed to buy and sell workflows to each other? Or should I simply collect those workflow patterns myself and use them to improve the model directly?

Users do not actually want to browse and choose workflows. They want one-step execution.

That means the best approach is still:

let the user use AI to build a workflow, refine it through natural-language feedback, and let me capture the workflow-construction data so the AI gradually learns how to design that workflow directly in one step.

## What are the elements required for AI to build a workflow?

If we think about human workflows in daily life, there are many standard workflow categories:

- coding
- marketing
- finance and tax
- legal work
- medicine
- finance
- scientific research
- sales
- e-commerce
- supply chain
- healthcare
- insurance
- creative design

If abstracted further, they seem to involve these stages:

- perception: continuously monitoring relevant data streams such as email, meetings, and files
- modeling: identifying what is a task and what is background knowledge
- strategic selection: choosing the best solution among multiple tools
- generation: producing the result
- evolution: updating strategy based on user clicks, edits, or feedback

So a complete workflow can be broken into:

1. receiving a task, which means there must be a trigger
2. planning, including what is needed and which tools should be called
3. intelligent execution
4. output
5. feedback and updating

## My current thinking

Right now I see at least two ways to approach this.

One resembles the current Codex pattern: you give it a task inside a task window, it solves the task, and once it completes it for the first time, you can ask it to generate a skill. The next time it sees a similar task, it calls that skill and executes the same workflow.

The workflow details are hidden from the user unless the user explicitly opens the skill file. But most users only care whether the task gets solved.

That said, there are still several missing pieces.

### 1. Data input and workflow triggering

Right now, I still need to manually input data and manually trigger the flow.

If the AI could embed itself inside other software, pull data on its own at the right moment, and trigger the process automatically, the user experience would be much better. It would feel more like an ERP system automatically acquiring data and dispatching operations.

This probably requires access through MCP-like integrations. But can software trigger AI in both directions through that kind of interface?

The data-acquisition and triggering model should be bidirectional:

- software tells AI that a new task has arrived and triggers it
- or AI triggers the task and fetches the data it needs

At a deeper level, the task is still being triggered by a human-designed structure.

So what is still missing is a very convenient trigger mechanism that allows software to connect to AI cleanly.

There should be an API layer that makes it easy for software systems to hand work to AI.

### 2. Agent decomposition and reuse

This workflow model does not yet embed other agents inside itself.

That creates a problem. If a task is too complex, it should really be split into multiple workflow agents, each responsible for a different part. The rule for decomposition is whether that agent can later be reused by other tasks.

If agents are reusable across tasks, the system starts to look more like a company architecture, and the workflow becomes more controllable.

The ideal design would be for AI to automatically decompose workflows according to demand.

That means we need workflow modules that can be called, assembled, and reused.

### 3. Tool calling

AI needs many tools in order to complete tasks.

The traditional method is to let AI simulate mouse clicks and use software as a human would. Typical tools include search and command-line interfaces.

The ideal method would be for those tools to expose direct interfaces for AI use.

But most companies probably will not expose those interfaces unless doing so expands their business or at least does not damage it.

Even so, web pages and desktop applications are already connected to backend data interfaces under the hood. So why not build a mapper that converts those UI interfaces into controllable software tools?

In fact, people have already done similar things. That means I may only need to integrate those tools rather than invent them from scratch.

### 4. Whether the result truly matches user expectations

Can AI ultimately generate outcomes that actually match what users want?

For example:

- replying to emails
- producing structured or unstructured outputs
- carrying out certain operations directly

## My current conclusion

Long-horizon planning, company-like multi-agent structures, and memory are all important, but they are not the most critical pieces for commercialization right now.

If the capabilities above are implemented well, they are already enough to solve most practical problems.

The final ability I still think matters a lot is:

RL capability, meaning the ability to learn through work itself.

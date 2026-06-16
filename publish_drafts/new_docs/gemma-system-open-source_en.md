# Building an Open System on Top of Gemma, Then Creating a Vertical Application in a Specific Domain

## Basic reflection

Right now, Gemma is still too large. Seven gigabytes is the size of a computer game. Just downloading it can take hours, and it also requires decent hardware.

But if it could become something preinstalled as part of an operating system, then the situation changes.

Then another question appears: doesn't that inevitably drag the problem into hardware?

I need to distinguish clearly between two things:

- building hardware
- building a system that runs on hardware

Those are not the same thing.

Selling a computer and selling a system that runs on a computer are also not the same thing.

So focusing on the system itself is probably the best choice. If the system is strong enough, people will naturally install it.

But the ecosystem on top of the system is still the most important part. Users matter. Developers building on top of it matter. Everything else in growth is secondary.

## What if OpenAI builds a super app?

Then the question becomes: how do you build something people cannot put down?

If OpenAI builds a super app that has memory, can operate a computer, and can operate a phone, then what do you do?

It seems like technologies similar to screen-casting control could already be enough to control computers and phones.

And what if they make it into an ecosystem where one single app is enough? You just connect your OpenAI account, tell the AI what you want, and it completes everything. The data all lives in the cloud.

And in fact, most app data already lives in the cloud.

If that is the world, then what advantage does an on-device Gemma system still have? Why not just download one app and let it automate things?

It also seems like OpenAI could build an ecosystem by letting other companies expose their applications for AI use. That sounds easier than integrating everything into a local operating system.

So what exactly is the advantage of the local model?

Cloud infrastructure also appears to have the advantage of huge storage and huge compute capacity.

When you think about phones today, outside of photography, networking, storage, and input/output, their raw compute power is not even what most people use directly. Most value comes from software running on top of the hardware.

So the real competitiveness of the phone seems to be software ecosystem.

That is why I think building hardware is a dead end. The real thing to think about is the software system.

And what does a system really do? At the deepest level, it connects hardware and software.

## What if the whole system becomes an app?

If the entire system becomes an app, while the phone mainly provides display and network, maybe that is not impossible either.

The best interaction style, or the laziest interaction style humans would prefer, is:

I give you an intention, and you directly complete it for me.

Something like a super butler that understands you extremely well.

If that is the standard, then maybe the local system itself does not have to be that powerful. A phone that can display, take photos, and connect to the internet, combined with one super app, might already be enough, even if that app is largely cloud-based.

Personally, what I want most is for it to take over all the operations that consume my intelligence and attention.

Because in real life, many things do not require very high intelligence. Most of them are procedural.

So I think the best system design should come from reversing the problem and asking: what is the laziest and most natural interaction style for humans?

## Commercial barriers may not matter that much

Commercial barriers may not actually help that much.

If OpenAI opened up its ecosystem today, countless developers would rush in immediately. It would not take long before stronger products than many current commercial products appeared.

At that point, many existing commercial players would probably stop resisting and simply join.

## What absolutely has to be local

There is one category that I still think has to remain local:

- AI vision
- AI voice

These two do not tolerate high latency well. The local experience is best.

And video transmission is extremely bandwidth-heavy, so it is hard to imagine it staying fully cloud-based forever.

If AI can see what you see, hear what you hear, and respond in real time like your shadow, then that is the strongest reason for local deployment.

That said, when I use the vision and voice modes built into major cloud models today, the latency does not always feel that high.

Even so, I still think local deployment matters because of:

1. bandwidth cost
2. battery cost
3. the fact that the network cannot be allowed to fail

## When on-device intelligence really becomes meaningful

The energy cost of transmitting bits is much higher than the energy cost of computing bits.

The real explosion of on-device AI probably happens when local models become good enough for most daily scenarios. They do not have to be extremely intelligent. They just have to be good enough.

And in most daily situations, some delay is actually tolerable. It is not like autonomous driving, where continuous real-time response is always required.

So when do you truly need constant vision and constant voice running all the time? In ordinary life, that seems rare.

In smart production or machine-control scenarios, it matters much more.

And in those scenarios, the hardware is usually attached to a physical host:

- a car
- a robot

The compute module moves with the machine. In that sense, the hardware and the tool it controls become one integrated body. It behaves more like an independent agent.

That is why I think on-device AI will split into two directions:

1. personal phones that people carry around, where large on-device models are not always necessary
2. machine brains, such as the brains of cars and robots

## If mobile on-device AI is the path, what is the real core?

Phones do have one advantage: CPU, GPU, and NPU are integrated, and the memory is unified.

So with enough optimization, it should be possible to run a reasonably capable model in a phone-sized device.

That makes the product shape clearer.

The role of the device-side system would be real-time perception and feedback, such as:

- AI vision
- AI voice input and output

If there is going to be an ecosystem, it will most likely still be built on Android, by adding new capabilities on top of the existing ecosystem and integrating the model more natively.

The most important infrastructure pieces seem to be:

1. memory
2. model perception, processing, and output
3. model control over applications

If those three things are done well, current model capability is already enough to build a breakout product.

## But then the harder question is: why are you the one who gets to build it?

If such a product is built, what happens next? Why would it be you who wins? Is there any way to actually succeed?

In reality, this kind of product would be attacked by app companies, because it would take away their traffic entrance and therefore their advertising revenue.

Phone manufacturers would definitely build their own versions. Unless your product is completely different from a phone, they may even block installation of your system.

So if your product is not good enough, and if you are not building a new hardware category yourself, then success is unlikely.

To really win, you would probably have to design your own hardware, and the product would have to be good enough to make people give up the AIOS built by phone manufacturers.

And all of the major giants are already thinking about this direction. If I can think of it, they can too.

## If someone really wanted to do it, what would be required?

There seem to be several conditions:

1. A fully self-designed AIOS and highly optimized hardware built specifically for it.
2. Heavy optimization around device-side models. The local model does not need to be extraordinary, but it must be good enough. It may even load extra capability from the cloud on demand. The design has to be upgradeable and pluggable.
3. A standard for intention interfaces. To get others to accept that standard, either you need enough users to force app companies to expose interfaces, or you need to build a framework that lets those companies still make money. For example, AI search results could show their ads, and they retain pricing power over their services. In that world, they may help you rather than resist you.

## A possible entry point

You would need absolute advantage in one specific domain.

One direction I can think of is serving elderly users.

Many older users cannot use ride-hailing, food delivery, or shopping apps well. If one sentence lets AI operate those apps for them, their children would probably be willing to pay for it.

And this is not just app operation. It is a true super-butler model.

The infrastructure pieces mentioned earlier become critical.

## Does an individual developer really have a chance?

Looking at it honestly, this is not really a lane designed for individual developers.

Unless the strategy is to improve and integrate existing hardware, package it extremely well, and act more like a product-driven assembler, in the style of Jobs, instead of designing and manufacturing everything from scratch.

## A deeper conclusion

After thinking more deeply, I arrived at a stronger conclusion.

Phones will probably deploy a small model locally, but that local model's role is mainly to save bandwidth from sending video to the cloud. It handles execution on the phone side, such as operating apps under instructions from a large cloud model.

So in that architecture:

- control and execution belong to the local model
- thinking and planning belong to the cloud model

Taken together, this suggests that mobile-side AIOS is fundamentally the game of major companies. Startups have almost no chance if they try to collide head-on.

## Additional judgment

Conversations with current AI also reveal something important:

AI still does not truly think deeply.

Once the context becomes long, it starts making things up, often in a very confident way. It does not actually understand the relationships between meanings inside events it has never seen before.

That is fatal in some domains, such as law and medicine.

Current AI still has a lot of room to improve because it is not yet real thinking in the strongest sense.

When Einstein discovered relativity, he could recall a formula he wrote ten years earlier and connect the pieces together.

Current models cannot really do that kind of delayed insight from the past.

In research and experimentation, knowledge and experience often have to be internalized over many years, until one day they suddenly connect and produce a breakthrough.

## Final thought

Right now, on-device systems still cannot run very large-parameter models. That depends on both hardware and software breakthroughs, and it will not happen in the short term, especially in embodied intelligence.

But even with today's model technology, many application scenarios are already deployable, and deployment is happening much faster than before.

So maybe this cycle did not really collapse. Maybe the bubble extended itself and pushed through the cycle in the short term.

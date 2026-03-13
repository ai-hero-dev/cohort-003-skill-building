# What is Ralph?

## From Multi-Phase Plans to Autonomous Agents

Think back to the mental model we had about multi-phase plans. The idea was to take huge chunks of work and break them down into smaller pieces that fit inside the smart zone of a context window.

![Diagram showing the multi-phase plans mental model](./screenshot-4.png)

To make this work, we needed to prompt the agent with three things:

1. **The destination** - where we're heading
2. **The journey** - the breakdown of all the tasks
3. **Do Phase N** - which phase to execute (phase one, two, three, etc.)

But there's a problem with this approach.

## The Human-in-the-Loop Problem

Someone has to sit with the LLM as it does all this work and say "okay, now go on to the next phase." The entire process requires a human in the loop (HITL).

However, not all tasks in a plan require human input. Many tasks can be done AFK (away from keyboard) where the human isn't involved at all. You might have felt this while monitoring an agent during its multi-phase plan - at certain points thinking "I don't really need to be here."

Once we have the PRD and understand the plan, the agent can really do its own thinking. We can QA it all at the end. The only thing you're needed for is to point it to the right phase. That's something a simple `for` loop can handle.

## The Quest for Autonomy

I'd been using multi-phase plans until December 2025 and they were okay but not amazing. I wanted to step away from the keyboard more and do other work while the agent was doing its thing. In other words, I wanted agents to be more autonomous.

Without really knowing it, I was looking for a framework that would help me do that.

Then I discovered [an article by Geoffrey Huntley](https://ghuntley.com/ralph) describing Ralph Wiggum as a software engineer. This idea gathered a lot of hype and has gone into the vernacular of people doing work with Claude Code.

People are calling out the weird little kid from The Simpsons and saying "yes, we use this as an AI coding technique." Even [Vercel said they "Ralph Wiggumed" webstreams](https://vercel.com/blog/we-ralph-wiggumed-webstreams-to-make-them-10x-faster) to make them ten times faster.

Ralph is just a simple loop.

You run Claude in a loop with a single prompt - the same prompt over and over again - getting it to do a task until it's complete.

## How Ralph Works

Instead of saying "do phase N," we ask the agent to walk through the journey itself.

| Multi-Phase Plans                         | Ralph                                   |
| ----------------------------------------- | --------------------------------------- |
| Give destination + journey + phase number | Give destination + journey              |
| Human directs each phase                  | Agent navigates all phases              |
| Human needed at start of each phase       | Human only needed at very start and end |

We give it the destination and our description of the journey, and then it just walks through until it completes.

This means instead of the human being needed at the start of each phase and at the end to QA the code, the human is only needed at the very start and the very end.

You can kick off a Ralph loop and it will loop and loop and loop until it's complete. Then it pings you and you can go and QA the code.

## How I'm Coding Now

This setup is how I'm doing most of my coding now. The flow tends to be:

1. Spend a lot of time creating the PRD and doing all the planning
2. Walk away
3. Come back to working code at the end (or mostly working code)

Even while filming this, I have a Ralph loop running in the background doing some work. Getting agents to work autonomously has been the goal of this course and all my work for the past few months.

Everything we've learned - from planning to feedback loops to steering - is really geared towards getting the agent to produce good results autonomously.

## Ralph is Fluid

As a final note: Ralph is a stupid name, and in certain ways, it's not even really a concept. Ralph is just a loop, and everyone has different implementations of that loop - different flavors in their Ralph loops.

I'm going to teach you something very different from the original vision. The original proposal preferred a much looser approach: just give the thing a PRD and let it run forever.

I prefer a version of Ralph where you control it a lot more. You give it more guardrails and a specific plan to follow as you go along.

There's no such thing as a right way to do Ralph. We're just trying to run an agent in a loop and get good results at the end.

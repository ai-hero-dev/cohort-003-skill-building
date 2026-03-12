There's a lot of people out there who are saying that the AI age is a new paradigm for software development. They argue that we need to chuck out all of our assumptions about how code works and what good code bases look like.

The reasoning goes like this: agents are fundamentally different from people, from human developers. They need entirely different guardrails and entirely different setups. In other words, the old rules are for boomers, and now we need to find new ways of building software.

## The "Code is Cheap" Thesis

Much of this thinking comes down to a single mantra: **code is cheap**.

When you have an AI agent that can basically churn out tons of code, the production of code becomes so much cheaper. So the argument goes that we don't need to worry that much about bugs anymore, because the AI will just be able to blast through code and create code faster than we've ever been able to see before.

The conclusion people draw: software quality matters less because you can just always churn your way out of software quality issues. If you have a bad code base, the AI would just be able to fix it by blasting out more code.

## Why This Is Wrong

I think this is incorrect.

I think that software quality matters **more** now, and that AI agents are **more sensitive** than humans to software quality. This massively affects how we should design our code bases and systems to take advantage of AI best.

But first, let me start off by defining what I mean by software quality.

**Is the code base easy to change?**

This definition comes from _The Philosophy of Software Design_ by John Ousterhout. John makes the argument that if a codebase is easier to change, then we can think of it as a better codebase.

![Holding up The Philosophy of Software Design by John Ousterhout](https://res.cloudinary.com/total-typescript/image/upload/v1773323077/ai-hero-images/ssrp5kgxlb03bamivoyk.png)

In other words:

- Is related information grouped together in the code base?
- How likely is it that a change you make to the code base will have unintended consequences that ripple outwards?
- What are the feedback loops like in the code base? If you make a change in one place and you accidentally cause a bug somewhere else, how likely are you to find out before you ship to production?

## Software Entropy

In a perfect world, we would always have perfect code bases. Our code bases would never be hard to change. They would always be well-designed and really easy to change with great feedback loops that we would always be able to catch bugs with.

But the truth is that most times, most people are touching a code base, they are making it worse, not better.

If you thoughtlessly make a change in a codebase to fix a bug or build a new feature, and you're not thinking about continually improving the code base or keeping it in this easy-to-change mode, then you are probably making that code base worse, not better.

This concept comes from _The Pragmatic Programmer_ and is called **software entropy**.

We can think of this kind of like a kludge meter where it just slowly rises with every single commit.

![Diagram showing the kludge meter rising and then being interrupted by a refactoring commit](https://res.cloudinary.com/total-typescript/image/upload/v1773323078/ai-hero-images/qput4iwkuvmblldb8xlt.png)

For anyone who's worked on any reasonable size of code base, this will ring true. Software developers don't work in a vacuum. There are pressures on you, there are time constraints, there are times when you just need to ship something immediately and you don't really care about the long-term consequences.

Or there are times where you're just having a bad day and you just need to get your work done. On those days, you're probably going to be having a negative effect on the quality of your code base, even though you're shipping features.

You can intervene and do refactors and redesigns that help stop the kludge. These might introduce a new part of the test suite or refactor the code to make it easier to change:

![Showing a commit that reduces the kludge meter](https://res.cloudinary.com/total-typescript/image/upload/v1773323078/ai-hero-images/d3bifhmjdithhhuijjjj.png)

But every commit that is not this thoughtful will eventually be increasing your software entropy again.

## AI and Software Entropy

In the AI age, AI massively increases the amount of commits you can do.

But currently, it does not do a great job at the entropy-saving commits. Figuring out a better software design to prevent software entropy is one of the hardest tasks a software engineer can do. It's harder than building new features. It's harder than fixing bugs.

And so it makes sense that AI is not very good at this yet. In its current state, **AI is a software entropy accelerator**.

## How AI Agents Learn From Your Codebase

This is especially true when you think of the three things that go into any AI coding session:

- The initial prompt (the thing that you're trying to get the agent to do)
- Any steering mechanisms you're using (like skills or CLAUDE.md)
- **Your code base** (the biggest one, the most important one)

Agents are much more likely to copy your codebase than any steering that you do because the codebase is the source of truth. If there are bad patterns in your code base, even if you're explicitly warning about them in your steering, it will tend to copy the code base by default.

This means that AI is maybe even more susceptible to kludge than human developers, because it will just blindly copy whatever's in your codebase without applying its own taste to it.

## The Statelessness Problem

An AI in a bad code base will have access to way fewer feedback loops, and so it won't know when it's writing bad code.

Humans, because they can develop memory about a bad codebase, can kind of survive it and work around it. And because they can understand what weird patterns a codebase has, they can produce fewer bugs and higher quality features within a bad codebase.

But AI, remember, is stateless. So again, it is more susceptible to a bad codebase than a human is.

It's a tale as old as time: you put garbage in, you're going to get garbage out.

## The Reality of Code Quality in the AI Age

So in my opinion, because software entropy is a fact of life, and because AI is just not really capable at the moment of creating these beautiful code-base saving commits, and because it's so unusually sensitive to code base quality, then I don't think we can say that code is cheap.

Cheap code will just accelerate you to the point where you've maxed out your kludge meter where the code base is complete garbage and impossible for an AI to change.

I know that you have worked in code bases like that. I have worked in code bases like that. And the only way you can get around it is by banging your head against the wall repeatedly until you're able to make the change or able to function within that code base.

AI, because it has no memory, has no chance.

In this section, we're going to talk about increasing the quality of your code through feedback loops, which are the essential way to prevent AI from increasing your software entropy.

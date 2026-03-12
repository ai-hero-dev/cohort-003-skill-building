By this point in the course, you've hopefully absorbed my context window paranoia. I'm constantly thinking about context, constantly thinking about the smart and dumb zones.

With current LLM capabilities, the best approach is staying within the early part of the context window. This works great for some tasks:

![Smart zone and dumb zone](https://res.cloudinary.com/total-typescript/image/upload/v1773315279/ai-hero-images/ygwo7gscorfngspalhxh.png)

Small features and bug fixes fit comfortably into a single context window. But what happens when you try to do something much larger?

## When Tasks Get Too Big

Consider a task that bursts its way into the dumb zone, like a major refactor. Or something where it's obvious that you won't be able to fit it into even a context window, let alone the smart part of the context window - like #4 below:

![Massive task](https://res.cloudinary.com/total-typescript/image/upload/v1773315280/ai-hero-images/n9aye0x5k0wuiiriozg9.png)

What do you do when you're faced with a task that's just too big?

The answer is the way developers have been doing it for decades: you take the big task and break it down into small tasks. That way, all of the work for this big task happens in the smart zone of the context.

![Smart task being broken down into smaller chunks](https://res.cloudinary.com/total-typescript/image/upload/v1773315280/ai-hero-images/yibrqstoyhbve168qruf.png)

## The Planning Problem

But here's the question: what kind of planning do you need to do to get this to work?

So far, our plans have only been the duration of a single context window. We haven't considered what it might look like to have documents spanning multiple context windows.

Fortunately, the community has coalesced around a common set of patterns. Specifically, two documents in particular.

## The Two Essential Documents

### PRD.md: The Destination

The first document you need is a description of the destination, the place you're heading.

If you don't know where you're heading, how on earth are you going to complete the task?

Some people call this the spec (specification for what you're building). Others call it a PRD (product requirements document). I'm using PRD here, but the name doesn't really matter.

Writing really good PRDs is an important skill by itself. Hammering out exactly what you want to build is super important and it scales to really large tasks. You can write PRDs for relatively small, manageable tasks too.

This is where you as the human get to impose your taste on the LLM and hammer out exactly what you're building. It has the same benefits as plan mode: you understand the project more, and the LLM understands the project more.

Except it can scale to much larger builds than just one context window.

### PLAN.md: The Journey

But there's a problem. If you only specify the destination, how does the LLM know how to break it down into small chunks?

Without a description of the journey, the LLM might just try to tackle everything in one big context window.

This is why you will often specify a `PLAN.md` file next to the PRD.

You use one session to create the massive destination, then you might use the same session (or clear the context) and create the journey as well.

You break down the product requirements document into a set of phases:

- Phase 1: do this
- Phase 2: do that
- Phase 3: and this
- Phase 4: and that
- Phase 5: and finally this

These phases are the three ingredients in your prompt. You're saying "we're going to do phase N", then you pass in the PRD and you pass in the entire plan.

## Why Passing The Whole Plan Matters

Passing in the whole plan is really useful because these phases don't step on each other's toes.

The LLM can see "we're doing that bit in phase 3, I'm not going to do that bit in phase 2". This prevents duplicate work and conflicting changes across phases:

![Showing Plan diagram again](https://res.cloudinary.com/total-typescript/image/upload/v1773315281/ai-hero-images/ukhgugcxyoopwpkhdtpe.png)

Learning how to build great PRDs, learning how to build great plans, and learning how to construct this prompt and navigate your way through these massive builds... That is the topic for this section. And it's a banger.

# Use Tracer Bullets in Our Multi-Phase Plan

## Running the plan through the agent

Let's run the plan and see what happens:

The agent is doing an explore phase, which is fantastic. It's exploring the codebase architecture, and we can see it's using the Sonnet 4.6 model, which is nice:

![Using Sonnet 4.6 for planning](https://res.cloudinary.com/total-typescript/image/upload/v1773321462/ai-hero-images/gug0rs42w1fe0pesex1p.png)

I always love it when the agent uses a cheaper model for these explore phases because it just seems like a good use of resources.

## The proposed phase breakdown

The agent has come back with a proposed phase breakdown. This is intentional design - it asks for feedback on the phases before it actually commits to building the plan out.

Phase 1 is much more interesting and very meaty:

- An analytic service
- An instructor route
- Summary cards

![Claude Code displaying the proposed phase breakdown in the terminal](https://res.cloudinary.com/total-typescript/image/upload/v1773321463/ai-hero-images/wooajeohnfxooje3d5z1.png)

This is a definition of a vertical slice - we're doing the service plus the route plus some UI as well.

Looking at the breakdown below, phase 1 is the tracer bullet that wires up the full stack with the simplest possible data: three summary numbers. Each subsequent phase extends the service and dashboard incrementally.

## Why tracer bullets work

This is exactly what we're looking for.

By the end of phase 1, we will know if the whole thing works essentially.

We'll understand:

- Whether we can connect the analytics service up to the instructor route
- What weird caveats are there
- All of the weirdness to do with this feature

In other words, all of the unknown unknowns will have been flushed out.

## Refining the phases

Looking at this immediately, five phases might be a bit too much. Phase 1 is packed in nicely - that's a good meaty amount. It might be too big, especially if we encounter any issues, but maybe it's okay.

However, we can group phase 2 and phase 3 together since they're both UI concerns. Phase 4 and phase 5 can also be grouped together.

So we'll ask the agent to group together phase 2 and phase 3, and then make another grouping for phase 4 and phase 5, resulting in three phases total.

![Claude Code showing the user feedback being entered into the terminal](https://res.cloudinary.com/total-typescript/image/upload/v1773321464/ai-hero-images/vtmbcuxamchimudeclj1.png)

```
Group together phase 2 and phase 3, and then make another grouping for phase 4 and phase 5, resulting in three phases total.
```

If we run that, it should give us a new set - a new plan.

## The plan file output

![Claude Code writing the plan file to the terminal](https://res.cloudinary.com/total-typescript/image/upload/v1773321465/ai-hero-images/yswzeoivekz2qgbyvsay.png)

The agent has spat out the plan file, `instructor-analytics-dashboard.md`. Beautiful.

Looking at the output, the phases down the bottom here are nicely laid out. We've got our three phases, and we can see a description of each phase - what to build and the user stories that they reference in the parent PRD:

![The three phases](https://res.cloudinary.com/total-typescript/image/upload/v1773321466/ai-hero-images/ys1ipjpn7zmwkiwdfi5f.png)

But we can see too that there's not a ton of implementation-like leakage inside here. The previous plan was almost an implementation just in pseudocode, but this is a lot more just text, essentially - it's a description of the feature.

## Durable decisions, not implementation details

The reason for this is that in the skill itself, I added some instructions to basically only make durable decisions that will definitely work across all phases.

Inside the skill, where it says "identify durable architectural decisions", we say:

> Before slicing, identify high-level decisions that are unlikely to change throughout implementation. In other words, we are planning what we can.

![Durable decisions inside the skill](https://res.cloudinary.com/total-typescript/image/upload/v1773321468/ai-hero-images/rje0bkjtxrafomz3j9kj.png)

You do want some implementation information in the plan itself because it helps keep everything on rails and means that what comes out is more predictable. But what we're saying here really is: don't plan what you can't plan.

Lots of stuff will only become apparent when you start actually going in and implementing it.

## What goes in the plan

Looking at the actual plan that we have, we can see the durable decisions are:

| Decision     | Details                                                                                                            |
| ------------ | ------------------------------------------------------------------------------------------------------------------ |
| Routes       | Instructor analytics at `/instructor/analytics` and admin analytics at `/admin/instructor/:instructorId/analytics` |
| Schema       | No changes - using existing tables like `purchases`, `enrollments`, `courseRatings`, and `courses`                 |
| Service      | A new analytics service pulling in authentication info and getting the current `userId` from the repo              |
| Dependencies | Very specific about what's being added                                                                             |

These are the kinds of decisions that are unlikely to change as we implement.

## The proof is in the implementation

Of course, the proof of the plan is in the pudding. We should actually go and implement this to see how it works.

Your plan may look different from this one. What did you notice about your plan that you liked or maybe didn't like? Is the level of detail too high or not high enough?

Share it in the [Discord](https://aihero.dev/discord) - I'd love to hear your thoughts.

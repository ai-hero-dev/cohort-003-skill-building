I'm really excited about this one because this lesson gives me a chance to talk about one of my favourite discoveries when working with AI over the past few months.

With just two well-chosen words, you can completely change the way that AI prioritizes tasks and the way that it plans.

These two words come from [The Pragmatic Programmer](https://www.amazon.co.uk/Pragmatic-Programmer-Andrew-Hunt/dp/020161622X), by David Thomas and Andrew Hunt. This is a 20-year-old engineering text with a ton of awesome insights.

We're going to steal two words from it: **tracer bullets**.

## Understanding Layers

The first idea behind tracer bullets is that systems have layers.

Layers might be different deployable units like we have here:

![A database, an API and a frontend](https://res.cloudinary.com/total-typescript/image/upload/v1773317135/ai-hero-images/mz2gag4r3rrvc3xb9p6q.png)

Or more likely, they're different services within the application, such as we have in our project.

Either way, these layers are things that you need to integrate in order to build something that works.

You might have a tiny feature which is front-end only. But more likely, you're going to have features that touch the front-end, the API, and the database, if they're going to be anything worth using for users.

## The Problem: Coding Horizontally

What I have noticed - and in fact what we noticed in our previous exercise - is that LLMs tend to code horizontally:

![LLM's code horizontally](https://res.cloudinary.com/total-typescript/image/upload/v1773317136/ai-hero-images/aynlqmpwv9ypwgeozg8c.png)

When they're designing the plan, they tend to think about it in terms of layers.

| Phase   | What Gets Built            |
| ------- | -------------------------- |
| Phase 1 | Analytic service plus test |
| Phase 2 | An entire component        |
| Phase 3 | An entire route            |
| Phase 4 | An entire other route      |

This is kind of crazy because we're not getting any feedback on whether the whole thing is working until we reach one of the later phases.

Sure, we've got some tests written for the analytics service in phase 1, but those tests are kind of meaningless if the design for the service is not going to match up to what we need in phase 3 or 4.

**We need early feedback and we need feedback as often as possible.**

## The Tracer Bullets Metaphor

To explain the metaphor, tracer bullets were what the anti-aircraft gunners in World War II used to put into their guns.

They would load in a special bullet every six rounds or so. Instead of firing an actual proper bullet that was meant to hurt the planes, it would just fire out a kind of phosphorescent beam from its backside.

The gunners would see these streaks of tracer streaking through the sky. It meant that the anti-aircraft gunners could look up, could see where their bullets were going, and adjust accordingly.

## The Solution: Vertical Slices

In code, this looks like this - instead of phases that span an entire layer, we now have phases that actually go through each layer:

![Vertical slices through the layers](https://res.cloudinary.com/total-typescript/image/upload/v1773317137/ai-hero-images/wjqnd9ebwmumk9hxdjs2.png)

Another name for this concept is **vertical slices**. Instead of just coding the horizontal stuff, we make sure each phase in the plan touches every layer.

| Approach                   | What Happens                  |
| -------------------------- | ----------------------------- |
| Horizontal (Problem)       | Each phase touches one layer  |
| Vertical Slices (Solution) | Each phase touches all layers |

That way we, as the human, are able to go in and take a look and provide feedback if needed.

But it also means our design actually encompasses all the layers that we need. And so we're less likely to make mistakes in our architecture because what we're building touches all the integration layers.

## Why This Works With AI

What makes this so cool to use with AI is that AI already knows what tracer bullets are. It's a relatively famous concept within software engineering.

All we need to do is just say the words `use tracer bullets` and maybe a little bit of brief explanation, and then the AI just gets it.

I have found that this massively improves the way that AI builds software, and we're going to use it throughout the rest of this course.

Hopefully this clicks for you, but if you have any questions, then do ask them in the Discord.

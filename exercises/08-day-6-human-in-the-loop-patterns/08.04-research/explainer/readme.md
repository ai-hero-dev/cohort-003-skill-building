There's a certain type of work you need to do with agents that can result in really expensive explore phases. For instance, you might need to integrate with an external service that you don't have the documentation for locally, or maybe a service where the documentation doesn't exist or isn't public.

## Understanding the Problem

When working through a Ralph loop across multiple context windows, the explore phase structure looks something like this:

- **Explore phase** - Research and discovery work
- **Implementation phase** - Actually building the solution
- **Testing phase** - Validating the code works

![Diagram showing context window with explore, implementation, and testing phases](https://res.cloudinary.com/total-typescript/image/upload/v1773386606/ai-hero-images/fp0seag1hhuplac103ta.png)

The longer and more expensive the explore phase is, the more you benefit from reducing it. This explore phase might be long because it needs to go to an external documentation site and fetch all the docs. Maybe it can't quite find what it's looking for and so it needs to continually search:

Over multiple runs, let's say you run this 10 times over a massive Ralph loop. This is just going to get really, really expensive.

![Diagram showing Ralph loop split across multiple context windows](https://res.cloudinary.com/total-typescript/image/upload/v1773386607/ai-hero-images/ggorfmtpnnjjras0kos2.png)

The solution? Reduce the size of these explore phases so you spend more time in the "smart zone" with less token spend:

![Diagram showing reduced explore phases for more efficient loops](https://res.cloudinary.com/total-typescript/image/upload/v1773386608/ai-hero-images/sandj6sgvap7lugvqj4i.png)

## The Research Phase Solution

One of the best ways to do that is to start off before you actually go into a Ralph loop with a research phase. In other words, you look at everything you need to do for the PRD, you take all of the external documentation and you cache it into an asset locally.

This typically takes the form of a `research.md` file.

![Example of research.md file](https://res.cloudinary.com/total-typescript/image/upload/v1773386609/ai-hero-images/eehnl5acyfh2regjqfwt.png)

It might be:

- Research about a specific external library or service you need to integrate with
- Research into a specific approach you want to take, like SSE versus WebSockets
- Any other upfront work that benefits all the Ralph loops afterwards

This approach won't be necessary for all tasks because not all tasks need a long, complicated explore phase. However, as your codebase grows and maybe gets harder to find the right things to actually pull into the context, a research phase at that point would be really, really handy too.

## Making Research a Human-in-the-Loop Task

Consider this research to be a human-in-the-loop task. Your taste is really important here.

For example, if you're trying to choose an external library to do a piece of work, your judgment going to influence the direction of the LLM's research. If the external service has multiple ways of doing the same thing, maybe it has some streams and maybe it has some webhooks, your taste is going to be really important for guiding which one goes into the `research.md`.

## Lifecycle Management

This research should have a lifecycle that's really closely monitored. You don't want this to stick around in the repo forever.

Why? Because:

- You might end up choosing a different implementation
- You might refactor away to a different service
- If the research is about your own code, your code might change

So it's really important to audit these `research.md` files in the same way that you audit your steering files, the same way that you audit your `CLAUDE.md` or your skills. A bunch of stale markdown files in your repo are going to really hurt your LLM's performance.

## Summary

Research is a way of caching explore phases to make sure you don't do expensive explore phases at the start of a bunch of Ralph loops. You've got to very carefully manage the files it creates. But if you do, you're going to get really, really nice results.

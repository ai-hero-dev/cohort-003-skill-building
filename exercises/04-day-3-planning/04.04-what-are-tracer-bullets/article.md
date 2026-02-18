# Tracer Bullets: Keeping AI Slop Under Control

In this article, I'm going to help you solve the slop problem by encouraging your AI agent to think in **tracer bullets**, small pieces of functionality that get built end-to-end.

It's a classic software technique that works incredibly well with AI.

## The Problem: Too Much Slop

AI has a natural inclination to sycophancy. It aims to please, in all aspects of its behavior. "You're absolutely right!".

In code, this means it wants to produce complete solutions all at once. It has in mind the idea for a finished file, or a finished feature, and it produces all of the code needed in one leap.

It doesn't stop to validate assumptions or get feedback. It just keeps going, building entire layers in isolation, without ever testing whether the critical path actually works.

The result? You end up with enormous chunks of code that need reworking. Slop. And there is a huge review burden on the developer to check all this crap.

### What This Looks Like in Practice

For example, you ask the AI to build a database service with an API that connects to it.

The AI builds:

- All the API endpoints (`GET`, `POST`, `PUT`, `DELETE`)
- Complete request/response models
- Error handling middleware
- Authentication logic
- Rate limiting
- Logging infrastructure

Only after all that does it try to connect to the database. And surprise, the connection string format is wrong. Or it's using an incorrect column type. Or the tests don't actually hit the database.

The pragmatic programmer calls this "outrunning your headlights.". The AI is building too much in the dark, without feedback loops to validate assumptions early. And you, the developer, end up with a huge mess to clean up.

## The Solution: Tracer Bullets

The concept of a **tracer bullet** comes from _The Pragmatic Programmer_. It's a small, end-to-end slice of functionality that touches all the layers of your system at once.

Instead of building horizontal layers in isolation, you build one tiny vertical slice:

1. Build a small feature end-to-end
2. Test it immediately
3. Get feedback
4. Move to the next slice in a fresh context window
5. Repeat

This approach solves the "outruns its headlights" problem directly. You get feedback loops built into the process instead of churning out features blindly.

And once you've tested that small slice, you can feel confident shipping features that work, rather than hoping the big layers all fit together.

### Forcing the AI to Think Small

You have to be extremely explicit with your prompt. AI's natural inclination is to build big layers in isolation. You need to make it do an end-to-end slice across all the vertical layers.

Here's a prompt you can add to your Ralph loop or a 'build-feature' skill to force the AI to think in tracer bullets:

```
## Tracer Bullets

When building features, build a tiny, end-to-end slice of the feature first, seek feedback, then expand out from there.

Tracer bullets comes from the Pragmatic Programmer. When building systems, you want to write code that gets you feedback as quickly as possible. Tracer bullets are small slices of functionality that go through all layers of the system, allowing you to test and validate your approach early. This helps in identifying potential issues and ensures that the overall architecture is sound before investing significant time in development.
```

## My Results With This Prompt

Here's a recent issue I worked on using tracer bullets with an AI agent:

```
Looking at the issue, I need to implement a "Reveal in File System" feature for videos. Let me break this down:

## Task Breakdown for Issue #161

1. **Tracer bullet**: Create backend endpoint that executes the PowerShell command to reveal a file in Windows Explorer from WSL
2. Add "Reveal in File System" to standalone videos context menu
3. Add "Reveal in File System" to video editor actions dropdown
4. Add "Reveal in File System" to sidebar video context menu

I'll start with the **tracer bullet** - creating the backend endpoint and wiring it up to one location.
```

Rather than building all four UI locations at once, I focused the AI on building just one end-to-end slice: the backend endpoint connected to a single UI location. This allowed me to validate that the core functionality worked before expanding it out.

## The Classics Have the Answers

Tracer bullets aren't new. Test-driven development isn't new. These are old concepts from old books, foundational ideas that have been formulating best practices for decades.

The problem? When new technology emerges, people get excited and forget to go back to the classics. They chase what's shiny instead of what's proven.

But the principles apply harder to AI than they ever did to humans. Context window constraints make the discipline non-negotiable. You can't ignore tracer bullets with an AI agent the way you might with a human developer. The consequences are immediate and visible.

## Bottom Line

The next time you're working with an AI agent, ask yourself: Am I letting it outrun its headlights? Am I getting it to validate assumptions early, or is it building in the dark?

Use tracer bullets. Force the agent to think small, build end-to-end, get feedback, and move forward with confidence.

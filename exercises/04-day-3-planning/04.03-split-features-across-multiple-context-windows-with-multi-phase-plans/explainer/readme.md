# Generate a Multi-Phase Plan From Your PRD

You've built a solid PRD that captures all the requirements for a large feature. But a PRD is just your destination, you still need a map for how to get there.

The challenge is that large features don't fit neatly into a single context window. You need to break them down into phases that Claude Code can tackle one at a time, each phase building on the last.

Right now, we're going to see what Claude Code naturally produces when you ask it to do this. Don't worry about whether it's perfect yet, that's the next lesson. For now, we're just observing.

## Steps To Complete

- [ ] Open a new Claude Code session inside your repo

Navigate to your repository and start a fresh Claude Code session.

- [ ] Reference your PRD from the previous lesson using the `@` symbol

Inside Claude Code, use `@` to pull in the PRD file you created in lesson 04.02. This gives Claude Code all the context it needs about your feature.

- [ ] Ask Claude Code to create a multi-phase plan

Use a simple prompt like this:

```
Turn this into a multi-phase plan and save it as a local Markdown file.
```

That's it. No additional specifications, no constraints, no guidance on how to break it down. Let Claude Code use its natural instincts.

- [ ] Watch what Claude Code produces

As the command runs, you'll see Claude Code explore the codebase and then generate a plan file. Take note of:

- How many phases did it create?
- What does each phase include?
- How big are the individual tasks within each phase?
- Does each phase seem to build on the previous one?
- Are there any tasks that feel too big or too small?

- [ ] Save or screenshot the generated plan

Keep the plan file that Claude Code creates. You'll be looking at it again in the next lesson when we talk about how to make it better.

This plan is your starting point. In the next lesson, we'll introduce a technique called tracer bullets that will help you refine it into something even more effective.
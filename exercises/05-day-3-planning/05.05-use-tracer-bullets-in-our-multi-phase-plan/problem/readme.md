# Use Tracer Bullets in Our Multi-Phase Plan

You've learned what tracer bullets are - a way to build a complete end-to-end slice of functionality first, then iterate outward. Now you're going to see how they reshape a multi-phase plan.

In the previous exercise, you created a naive multi-phase plan for your PRD. That plan probably breaks work down logically, but it doesn't necessarily account for how you'll validate that pieces work together as you build.

A tracer bullet skill, one that explicitly instructs Claude to think in terms of feedback loops and integration checkpoints, will generate a significantly different plan. Your job is to use that skill and compare the two approaches side by side.

## Steps To Complete

### Integrate the Tracer Bullet Skill

- [ ] Open a fresh Claude Code session with zero context

This ensures the LLM won't be influenced by the previous plan when generating the new one.

- [ ] Delete your naive multi-phase plan from the previous exercise

You'll find this in `plans/` directory. This is an important sanity check - we want to test the tracer bullet skill in isolation.

- [ ] Pull the `prd-to-plan` skill into your repository

This skill is already written and ready to use. It has copious mentions of tracer bullets built into its instructions.

### Generate Your Tracer Bullet Plan

- [ ] Open Claude Code and invoke the skill

```
/prd-to-plan @prd/your-prd-file.md
```

Pass in the same PRD you used before. Tab to auto-complete if needed.

- [ ] Run the skill and wait for the output

Claude will explore your codebase, then propose a phase breakdown with tracer bullets in mind.

### Compare and Observe

- [ ] Place your tracer bullet plan alongside the naive plan you created earlier

You might want to open both files side by side in your editor, or copy the old plan somewhere temporarily so you can reference it.

- [ ] Notice the differences between the two plans

Don't over-analyze, just observe. Look for patterns:

- Does the tracer bullet plan break work into smaller, more granular steps?
- Are there explicit validation or QA checkpoints built into the phases?
- Does the tracer bullet plan call out integration points where you can test the full stack earlier?
- Are there earlier feedback loops - places where you can verify things work before moving forward?

- [ ] Write down 3-4 specific differences you observe

These don't need to be lengthy. A sentence or two per observation is enough. Focus on:

- Where feedback loops appear (earlier in the tracer bullet plan?)
- Where QA or integration validation happens
- How the phase boundaries differ between the two approaches

### Reflect

- [ ] Think about why these differences matter

The tracer bullet plan is shaped differently because it expects you to validate during execution, not just at the end. This matters because you'll catch problems while you're still building, not after all phases are done.

You won't execute this plan yet, that's the next lesson. But notice how the plan itself is designed to give you feedback checkpoints along the way.
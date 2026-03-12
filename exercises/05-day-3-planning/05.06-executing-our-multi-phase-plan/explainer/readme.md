# Executing Our Multi-Phase Plan

When you've got a solid PRD and a multi-phase plan with tracer bullets, the real fun begins. You get to watch Claude Code execute your specification while you maintain control through strategic feedback.

But there's a discipline to this process. Each phase follows a natural rhythm.

That's where the **plan-execute-clear loop** becomes critical.

## The Rhythm of Multi-Phase Execution

Each phase follows the same pattern:

1. **Explore** - Claude explores the codebase to understand patterns and requirements for that specific phase
2. **Implement** - Claude builds the feature or functionality outlined in the phase
3. **Review** - You manually QA the work and give feedback in the same context window
4. **Iterate** - Claude refines based on your feedback until you're satisfied
5. **Clear** - You intentionally clear the context and start fresh for the next phase

This rhythm prevents context degradation. You're not trying to fit all three phases into one conversation. You're giving Claude a focused job, watching it complete that job, then starting completely fresh.

## Steps To Complete

### Phase One Setup

- [ ] Open your project in Claude Code

You should have both your PRD and multi-phase plan ready to reference. If you don't, go back to lesson 04.05 and complete the tracer bullets exercise first.

- [ ] Start a new Claude Code session and clear the context

Use `/clear` to start with a blank slate. You want to begin phase one with maximum context available.

### Execute Phase One

- [ ] Paste your PRD and plan files, then ask Claude to execute phase one

Use the `@` syntax to reference your PRD and plan files. Your prompt should be simple:

```
@prd/your-prd-file.md @plans/your-plan-file.md Do phase 1
```

Don't use plan mode here. You want Claude to start working immediately. It will likely explore the codebase first, then begin implementation.

- [ ] Let Claude complete the explore and implementation phases

You should see Claude working through discovery, reading files, understanding the patterns in your codebase. Let it run until it finishes the implementation work for phase one.

### Review and Iterate

- [ ] Review what Claude built

Actually run the code. Test it. Look at the files it created. Does it match your specification? Are there bugs or missing pieces?

- [ ] Give Claude feedback in the same context window

If something needs fixing, describe what's wrong and ask Claude to refine it. If it's mostly right, say so. Iterate until you're happy with phase one.

- [ ] Commit your work

Once phase one is complete and tested, make a git commit. This gives you a safe checkpoint to return to if something goes wrong in phase two.

### Move to Phase Two

- [ ] Clear the context intentionally

Close this conversation. Don't continue to phase two in the same context window. This is the discipline that keeps you sharp.

- [ ] Start a fresh Claude Code session for phase two

Clear the context again. Paste your PRD and plan files. Ask Claude to do phase two:

```
@prd/your-prd-file.md @plans/your-plan-file.md Do phase 2
```

Claude has a fresh context budget. It will re-explore what it needs to know, then execute phase two without the baggage of phase one taking up tokens.

- [ ] Repeat the review-iterate-commit-clear cycle for each phase

Each phase gets the same treatment. Explore, implement, review, iterate, commit, clear.

- [ ] After your final phase, run the full test suite and type-check

Make sure nothing is broken across all phases. The clearing strategy should have prevented context degradation, but verification is important.
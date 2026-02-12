# The Plan/Execute/Clear Loop in Action

You've learned what plan mode is and how to use it in Claude Code. Now it's time to put that knowledge to work by actually building something.

In this exercise, you'll build a comment system for a learning platform. Students can leave comments, and instructors or admins can hide certain comments and view them in a separate space. This is a real feature with moving parts: database schema, API endpoints, component structure. This makes it perfect for practicing the plan/execute/clear loop.

The goal isn't just to build the feature. It's to get comfortable with how planning, executing, and clearing context work together in practice.

## Steps To Complete

### Enter Plan Mode and Scope the Work

- [ ] Press Shift+Tab twice to enter plan mode in Claude Code

This puts you in the planning phase where you're thinking, not coding.

- [ ] Have a conversation with Claude Code about what you want to build

Discuss the scope. You can build a simple comment system, or you can add instructor/admin features, comment hiding, comment stats, or whatever else interests you. Use this conversation to settle on what you're actually building.

- [ ] Walk through the design decisions with Claude Code

Talk about:
- Database schema
- Routes and API endpoints
- Component structure
- How visibility rules will work (who can see what)
- Any other architectural decisions

- [ ] Review the plan or let Claude Code know you're ready to move forward

You don't have to review the written plan, but you should have a gut feeling that you and Claude Code are on the same page about what you're building.

### Execute the Build

- [ ] Press Shift+Tab once to enter execution mode

Claude Code will offer you a choice: clear the context and use just the plan, or keep the context and continue. Check your context meter in the status line.

- [ ] Make a context decision

If you've used a lot of context in planning (say, 60%+ of your budget), clear the context and work from the plan. If you're still under 20-30%, you might keep the context and move forward. Watch that meter like a hawk.

- [ ] Ask Claude Code for its implementation plan for the first feature

Don't just say "build it." Ask Claude to walk you through how it's going to tackle the feature, then iterate on that plan until it sounds sensible.

- [ ] Let Claude Code build, but stay alert

You're mostly watching now. If Claude Code does something that looks wrong, uses a strange library, writes obvious bugs, doesn't match your design decisions, or doesn't fit the project's existing patterns, press Escape and steer it back on track.

Things to watch for:
- Hallucinated libraries or dependencies
- Code that doesn't match the rest of your project
- File naming or casing that breaks conventions
- Logic that doesn't match your design

### Test, Review, and Decide What's Next

- [ ] Test the feature end-to-end

Make sure the comment system works as you scoped it. Students can leave comments. Instructors/admins can hide them and view them separately. Everything functions.

- [ ] Review the code

Check that it's clean, follows your project's patterns, and does what you intended.

- [ ] Check against your scope

Did you build everything you said you would? Are there obvious bugs or missing pieces?

- [ ] Decide if you need another cycle

If you find bugs or incomplete features, you can either clear context and start a new plan-execute cycle, or, if you still have context budget left, keep going and fix things in the current window. Your choice depends on how much context you've used and how much work remains.

### Handle Context Overflow (If Needed)

- [ ] If context gets scary, dump your progress

Ask Claude Code to output:
- The current plan
- A progress report (what's been done, what's left)
- Everything else relevant to continuing

- [ ] Clear the context with `/clear`

- [ ] Restart from the artifacts

Point Claude Code at the saved plan, progress report, and the changed files in git. It should be able to pick up where you left off.

You probably won't need this for a simple comment system, but it's a useful escape hatch if scope gets bigger than expected.
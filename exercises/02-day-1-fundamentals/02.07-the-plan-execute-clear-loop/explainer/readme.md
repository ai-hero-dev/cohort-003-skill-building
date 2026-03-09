# The Plan-Execute Loop

You now understand how Claude Code works. You've learned about plan mode and set up context percentages in your status line. You're ready to kick off the plan-execute loop.

This feature lets you add lesson comments where students can discuss lesson content. Instructors can moderate by deleting comments. It's a great playground to experiment with plan mode - you can keep it simple or add moderation dashboards, permission systems, and more.

The point is to use a small prompt and watch how Claude Code turns it into a real, fleshed-out plan.

## Steps To Complete

### Setting Up Your Session

- [ ] Open Claude Code and start a fresh session

Clear your previous work with `/clear`.

- [ ] Write a simple prompt requesting the feature

```
Make it so that students can comment on lessons and instructors can moderate their comments.
```

Keep it brief. The goal is to see how well Claude Code can expand a simple idea into a detailed implementation plan.


### Planning Phase

- [ ] Enter plan mode by pressing Shift+Tab twice

Watch the status line show `plan mode on`. Claude will begin exploring your codebase and designing the implementation.

- [ ] Watch Claude ask clarifying questions

Claude will interrogate design decisions with you. Answer each question honestly:

- Should comments be editable?
- What happens when a comment is deleted (soft delete vs hard delete)?
- Who can see comments (enrolled users only, or everyone)?
- Should comments be flat or threaded?
- How should they be sorted?
- What's the character limit?
- Where should the comments section appear?

Write down your answers as Claude asks.

- [ ] Review the generated plan

Once Claude finishes asking questions, it will output a detailed plan in your plan file. Read through it carefully. Does it match your vision? If not, ask Claude to adjust specific sections.


### Execution Phase

- [ ] Exit plan mode and move to execution

Press Shift+Tab once to cycle out of plan mode and into execution mode. Claude will ask whether to clear context or keep it. If you're still in the smart zone (under 40% context), you can keep everything. If you're approaching the dumb zone, consider clearing context and starting fresh with just the plan.

- [ ] Let Claude build while you watch

Claude will start implementing the feature step by step. Your job is mostly passive - watch the execution unfold. Claude will add the database schema, create services, update routes, build UI components, and seed test data.

- [ ] Stop and steer if something looks wrong

If Claude does something you don't like, press Escape to pause. Common issues to watch for:

- Using hallucinated libraries that don't exist in your project
- Obvious bugs or syntax errors
- Code that doesn't match your project's patterns or conventions
- File naming that breaks conventions (wrong casing, wrong location)

When you spot a problem, describe what should happen instead and let Claude course-correct.

- [ ] Let type checking and tests run

Claude will run `npx tsc --noEmit` and `npm test` to verify everything works. Watch for any failures. If tests pass and types check, you're in good shape.


### Observing and Reflecting

- [ ] Observe the context window throughout

Watch how the context percentage grows as Claude explores files and generates the plan. Take note of when it spikes - this helps you understand what Claude is doing behind the scenes.

During execution, watch how quickly context climbs. The solution video shows jumping from 35% to 48% by the end - notice how fast that happens when Claude is actually building.

- [ ] Write down your observations

Record what you notice:

- How much context did exploration use?
- Did Claude ask questions you didn't expect?
- Did the plan surprise you with ideas you hadn't considered?
- How long did the entire planning phase take?
- How much context was used during execution?
- Did Claude build things in the order you expected?
- Were there any bugs or issues that needed steering?
- Did you feel confident letting Claude build, or did you want to intervene?

- [ ] Test the feature manually

Log into the app as different users (students, instructors, admins) and verify the comments system works as designed. Try posting comments, deleting them, and checking that permissions work correctly.

- [ ] (Optional) Ask questions in the Discord

Share your observations and any questions with the cohort. What behaviors did you notice? What would you do differently next time?
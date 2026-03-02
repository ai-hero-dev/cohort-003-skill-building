# Write Great PRDs With This Skill

## Introduction

A PRD is your way of describing the destination for a long, multi-context-window session. But how do you write one? What should you include? How do you even put it together?

These are open questions, and you'll develop your own style over time. But there's a skill that can help guide you through the thinking process, one that asks relentlessly about every aspect of your plan until you really understand what you're building.

In this exercise, you're going to use the `write-a-prd` skill to turn a rough feature idea into a complete, well-scoped PRD. You'll see how clarity in requirements emerges from disciplined thinking, not upfront perfection.

## Steps To Complete

### Set Up Your Session

- [ ] Open a fresh Claude Code session

- [ ] Invoke the `write-a-prd` skill by typing `/write-a-prd` and tabbing to autocomplete

### Describe Your Feature Idea

- [ ] Describe the instructor analytics dashboard to Claude

You can be vague at first. Mention that instructors should see revenue trends, enrollment numbers, completion rates, quiz pass rates, and where students drop off. Let Claude guide you from there.

### Walk Through the Interrogation

As the skill runs, Claude will ask you a series of questions about:

- Which metrics matter most
- Who needs to see what data
- How the interface should be organized
- What time periods make sense for filtering
- Edge cases (no courses yet, no revenue yet, etc.)

- [ ] Answer each question honestly

Don't overthink your answers. The skill's job is to surface what you haven't thought through yet. When Claude asks something you haven't considered, that's the moment the skill is working.

- [ ] Let Claude challenge your thinking

If you say "instructors should see all metrics," Claude might ask: "Should the dashboard show all 22 metrics on one page, or should we prioritize?" These challenges are features, not bugs.

### Review the Module Breakdown

Claude will propose the modules needed to build this feature:

- [ ] Check that the proposed modules make sense

Do they match how you'd structure the code? Would you add, remove, or restructure anything?

- [ ] Confirm whether the modules should have tests

The skill will remind you of project conventions. Decide what makes sense for your codebase.

### Accept the Finished PRD

Once Claude finishes writing the PRD, it will output it as a local file.

- [ ] Review the finished PRD

Read through the entire PRD. Does it capture what you want to build? Is the scope clear? Are there surprising decisions encoded in the Implementation Decisions section?

- [ ] Note any thoughts or reactions

What surprised you? What would you change? What clarity did the interrogation give you that you wouldn't have gotten otherwise?

This note-taking is optional, but valuable, especially if you're going to use this PRD in the next lesson to break the feature into phases.
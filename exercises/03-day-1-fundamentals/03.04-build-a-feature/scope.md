# Scoping Document: Build a Feature

## Scope

Guide learners through their first hands-on experience building a feature with an AI coding tool, focusing on the practical workflow of prompting, observing, and iterating—not perfection on the first try.

## Prerequisites

- Completed 01.02 (Codebase Exploration) — learner can navigate the repo structure
- Understands the basic concept of what they're building (a course review system)
- Has Claude Code set up and ready to use
- Familiar with the concept of context windows (from 01.01)

## In Scope

- How to start: write a 1-2 sentence prompt using dictation (talk it out, don't overthink)
- Observation phase: watching the AI's natural instincts before steering it
- Context awareness: using `/usage` to monitor token consumption and identify the "dumb zone" (~80K tokens/40% of window)
- Transition to building: when to flip to "accept all edits" mode (shift+tab)
- Testing the full feature flow: submit → save → display
- Basic debugging cycle: identifying broken functionality and working with the AI to fix it
- Maintaining context hygiene throughout the entire build process

## Out of Scope

- How to steer the AI with agents.md or skills (covered in Day 2)
- Plan mode or multi-phase planning (covered in 01.05 and Day 3)
- Advanced debugging patterns like red-green-refactor (covered in Day 4)
- Detailed architectural decisions or deep design thinking
- Writing comprehensive PRDs or specifications upfront
- Any customization of the AI's behavior beyond defaults

## Teaching Sequence

1. **Starting with a lightweight prompt** — why 1-2 sentences is enough, using dictation removes friction
2. **Observing before intervening** — the learner should watch what Claude naturally does without steering yet, taking notes on approach and choices
3. **Context as a real constraint** — explaining the `/usage` command and the 80K token threshold where quality degrades
4. **Shifting to build mode** — recognizing when confidence is high enough to flip to accept all edits
5. **Testing the full flow** — concrete verification that the feature works end-to-end
6. **Debugging in the conversation** — treating issues as part of the natural build cycle, staying in dialogue with the AI
7. **Keeping context in view** — reinforcing that context management is a continuous concern throughout, not a one-time check

---

**Note:** This lesson is intentionally narrow—it's about _starting_ and _completing_ a first feature, not mastering advanced techniques. The goal is confidence and momentum, not perfection.

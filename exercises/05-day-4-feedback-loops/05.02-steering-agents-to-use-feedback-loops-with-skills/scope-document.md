# Scoping Document: Steering Agents to Use Feedback Loops With Skills

## Scope
Write a reusable skill that encodes your execution discipline (explore → implement → test → commit) so Claude follows the same structured loop every time, removing the friction of repeatedly steering it toward feedback loops.

## Prerequisites
- Learner understands *why* feedback loops matter (Lesson 05.01)
- Learner can write and invoke skills (Lessons 02.03, 02.04)
- Learner can read and interpret agent execution output (from Days 1–3)
- Learner is familiar with the notifications feature from the project README

## In Scope
- **Authoring the skill**: Writing clear instructions that prescribe a structured execution loop (explore → implement → feedback loops → commit)
- **Invoking the skill**: Using it to execute one pre-written phase of the notifications feature
- **Observing execution**: Reading through agent commits and output to verify the loop was followed
- **Light iteration**: If the agent deviated from the discipline, tweaking skill wording (1–2 passes maximum)
- **Optional personal opinions**: Showing how to add preferences (commit message format, testing approach) into the skill, but treating this as secondary

## Out of Scope
- **Planning**: You provide a pre-written plan; learners do not break the feature into phases themselves
- **Full feature execution**: Only prove the skill works on one phase, not the complete notifications build
- **Red-green-refactor deep dive**: That pattern gets its own lesson (05.04)
- **Pre-commit hooks**: Covered separately as an enforcement mechanism (05.03)
- **Comprehensive style guide**: Learners add their own opinions incrementally; not a focus here
- **Codebase planning**: Planning learners already did in 03.02–03.03; this is not a re-teach

## Teaching Sequence

1. **Recap the friction** — feedback loops work, but you have to remind Claude each time; that's overhead
2. **Introduce the skill concept** — encode your discipline once, reuse it on any feature/phase
3. **Show the pre-written plan** — here's the notifications feature already broken into phases
4. **Author the skill together** — what do "explore," "implement," "test," and "commit" actually mean as concrete instructions?
5. **Invoke the skill on phase 1** — let Claude execute using the skill
6. **Observe and verify** — did Claude follow the loop? Did it catch bugs? Where did it deviate?
7. **Iterate if needed** — if execution went sideways, add clarity or specificity to the skill (optional, light touch)
8. **Conclude** — you now have a reusable execution template that travels with you through the rest of the course

---

**Key principle**: This lesson is about *skill authorship for execution discipline*, not feature building or planning. The notifications feature is the *canvas*; the skill is the *learning outcome*.
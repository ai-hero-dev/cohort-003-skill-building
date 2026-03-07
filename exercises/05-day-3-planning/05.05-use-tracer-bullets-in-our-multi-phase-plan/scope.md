# Scoping Document: Use Tracer Bullets in Our Multi-Phase Plan

## Scope
This lesson teaches learners to generate a significantly better multi-phase plan by integrating a pre-built tracer bullet skill into their prompting workflow, then comparing the new plan against their naive baseline to see how tracer bullets reshape plans around feedback loops and integration validation checkpoints.

## Prerequisites
- Understanding what tracer bullets are and why they matter (04.04)
- A naive multi-phase plan created in the previous exercise (04.03)
- A PRD from an earlier exercise (04.02)
- Basic familiarity with integrating skills into Claude Code (from 02.03 and 03.02)
- Comfort with the prompt-skill-context workflow from earlier day 2 exercises

## In Scope
- Integrating the pre-built tracer bullet skill into the repository
- Re-prompting Claude with the same PRD, but now contextualizing the request with the tracer bullet skill
- Side-by-side comparison of the naive multi-phase plan vs. the tracer-bullet-informed plan
- Noticing and naming 3-4 key differences: earlier feedback loops, explicit QA checkpoints at integration points, validation opportunities *during* phases rather than after
- Brief observation that this plan shape enables catching problems during execution, not at the end

## Out of Scope
- Executing or implementing the plan (that's 04.06)
- Building or modifying the tracer bullet skill itself (skill-building was 02.04)
- Deep analysis of *why* these differences matter mechanically — the proof comes in actual execution
- Creating new PRDs, re-scoping features, or revisiting 04.02
- Comparing tracer bullet vs. non-tracer bullet approaches at a theoretical level — this is hands-on observation only

## Teaching Sequence
1. **Show the baseline** — Display the naive multi-phase plan from 04.03 side-by-side so learners have a reference point
2. **Integrate the skill** — Walk through pulling the pre-built tracer bullet skill into the repo and contextualizing it
3. **Re-prompt with the skill** — Use Claude Code to regenerate a multi-phase plan with the same PRD, now with the skill in context
4. **Compare and notice** — Place the two plans side-by-side and let learners observe the differences naturally (don't over-explain)
5. **Name what changed** — Call out the recurring patterns: where feedback loops appear, where integration validation happens, where QA checkpoints are embedded
6. **Tee up execution** — Brief reflection: this plan is shaped differently because it expects to validate *during* work, not after — execution proof coming next

---
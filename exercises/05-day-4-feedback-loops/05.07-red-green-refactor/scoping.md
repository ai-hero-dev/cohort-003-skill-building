**Scope Summary**

**Lesson title**: Red-Green-Refactor (Skills Practice)

**Core takeaway**: Use the red-green-refactor skill to build a real feature, observe the test-first discipline in action, and develop judgment about whether the tests Claude produces are meaningful and well-designed.

**Prerequisites**:

- Learner understands what red-green-refactor is and why each phase matters (04.04)
- Learner can identify characteristics of good tests: they test behavior (not just implementation), fail meaningfully when code breaks, and verify the specific requirement without over-specifying how it works (04.04)
- Learner is familiar with writing PRDs (03.02)
- Learner understands multi-phase planning (03.03-03.06)
- Learner can steer agents with agents.md (02.01-02.02)

**In scope**:

- Pre-written PRD for a single, focused feature: instructors get notified when someone purchases the course
- Pre-written plan/execution strategy for the learner to reference
- Learner invokes the RGR skill pointed at the PRD
- Learner observes the red-green-refactor cycle happening in real-time
- Learner evaluates the tests being written: Are they testing behavior? Do they fail meaningfully? Are they over-specified or under-specified?
- Learner may need to steer the skill mid-execution if it drifts (using agents.md knowledge) to get it back on track
- Learner reflects on test quality and identifies what Claude did well or poorly

**Out of scope**:

- Writing the PRD from scratch (pre-provided)
- Writing the plan from scratch (pre-provided)
- Deep debugging of test failures (if the skill breaks badly, that's a sign it wasn't ready for this exercise — learner documents but doesn't fix)
- Building additional notification scenarios (focus is on one feature, one cycle, one quality assessment)
- Introduction to the RGR skill itself — assume it's already set up and available
- Playwright or E2E testing concepts (that's 04.06)

**Teaching sequence**:

1. **Context & Goal** — Remind learner what RGR is and what good tests look like (refresh from 04.04). Today they'll see it in action.
2. **Review the PRD** — Walk through the notification feature requirement together. What needs to be true when this is done? (Sets expectations for what tests should verify)
3. **Review the Plan** — Show the preset execution strategy so learner knows what Claude will attempt to do.
4. **Invoke the Skill** — Learner runs the RGR skill pointed at the PRD. They're now an observer and active steerer.
5. **Watch Red Phase** — Observe Claude writing the failing test. Pause and ask: "Does this test clarify what 'done' looks like? Does it test the right behavior?" (Applying the judgment framework from 04.04)
6. **Watch Green Phase** — Observe Claude writing the simplest code to pass. Does it feel rushed? Is it readable enough? (Judgment call, not perfection judgment)
7. **Watch Refactor Phase** — If it happens, observe Claude improving the code. Does the test still pass? (Reinforces why tests matter)
8. **Steering Moment** — If the skill goes off-track (writes bad tests, ignores the PRD, etc.), learner uses agents.md knowledge to steer it back. This is active problem-solving, not passive observation.
9. **Reflection** — After the feature is "done," learner reflects: What was the quality of the tests? Where did Claude excel? Where did it stumble? How did the test-first approach discipline the implementation?
10. **Comparison** — (Optional) Show what this would have looked like if Claude had written the code first and tests after. What would be different?

---

**Key Design Notes:**

- The PRD and plan are **pre-written and preset** so learner's cognitive load is on _observing and judging_, not planning.
- The learner is **actively involved** (can steer) but the skill is doing the heavy lifting.
- The focus is **test quality assessment**, not "did we build the feature perfectly."
- One notification scenario is enough — the learner walks away with a felt sense of how RGR works and what to look for in tests.

---

Does this match what you're building?

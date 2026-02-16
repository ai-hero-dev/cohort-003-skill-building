# Scoping Document: The Plan-Execute-Clear Loop

## Scope
Learn how to use Claude Code's plan-execute-clear workflow to build a comment system feature by cycling through planning, execution, and context management phases.

## Prerequisites
- Understanding of what plan mode is and how to activate it (Shift+Tab twice)
- Knowledge of how context usage appears in Claude Code's status line
- Familiarity with Claude Code's basic interface and navigation
- Experience with basic full-stack web development concepts (database, API, UI)
- Completion of lesson 01.05 (What is Plan Mode)

## In Scope
- **Entering plan mode** — How to activate it (Shift+Tab twice) and start a planning conversation with Claude Code
- **Scoping with Claude Code** — How to define feature scope and complexity collaboratively before writing code
- **Design decisions in planning** — Walking through database schema, routes, API endpoints, and component structure
- **Recognizing "plan readiness"** — Understanding when you and Claude Code are aligned enough to move to execution
- **Context awareness during execution** — Monitoring the status line context meter and making decisions about when to clear
- **The execute phase** — Letting Claude Code build while watching for hallucinations, bad libraries, bugs, or code that doesn't match the design
- **Intervention during execution** — Pressing Escape to stop and steer Claude Code mid-execution when needed
- **The clear and restart pattern** — Dumping plan + progress report to files, using `/clear`, and restarting from artifacts + git diff
- **Final validation** — Testing, code review, and checking that implemented features match the original scope
- **Deciding on re-planning** — When to cycle through another plan-execute-clear loop vs. finishing

## Out of Scope
- Multi-phase plans for massive features (covered in 03.03)
- Advanced steering techniques with agents.md files (covered in 02.02)
- Feedback loops and testing strategies (covered in Day 4)
- Tracer bullets and phase-gating (covered in 03.04-03.05)
- Using Ralph for AFK coding (covered in Day 5)
- Refactoring patterns (covered in 06.01)

## Teaching Sequence
1. **Activate plan mode** — Start by showing Shift+Tab twice to enter plan mode; establishes the entry point for the entire workflow
2. **Have the scope conversation** — Talk through what you want to build and let Claude Code suggest design decisions; builds shared understanding before any coding
3. **Walk the design tree** — Iterate on Claude Code's implementation plan until it feels right; ensures both parties are aligned on approach
4. **Recognize readiness** — Explain the "gut check" moment when you know Claude Code understands what you need; avoids over-planning
5. **Transition to execution** — Hit Shift+Tab once and watch the context meter; introduces the decision point about clearing
6. **Let Claude build with oversight** — Explain passive watching and active steering; builds confidence in letting the AI work
7. **Spot and fix problems** — Identify hallucinations, bad choices, bugs, and misaligned code; teaches critical evaluation during execution
8. **Test and review** — Walk through final validation of the built feature; closes the loop with completeness check
9. **Know when to cycle** — Decide whether bugs or incomplete features warrant another plan-execute-clear loop or finishing; establishes judgment for next steps

---

**Note:** This lesson is hands-on and project-based. The teacher should build a real comment system (with optional admin hiding and viewing features) while narrating the plan-execute-clear workflow, not just explaining it theoretically.
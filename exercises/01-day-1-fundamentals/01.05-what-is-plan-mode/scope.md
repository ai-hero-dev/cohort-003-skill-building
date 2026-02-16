# Scoping Document: What Is Plan Mode?

## Scope

Introduce plan mode as a foundational technique that solves the core problem of AI code quality — by forcing the agent to explore and understand a codebase thoroughly _before_ writing any code, you get better results and clearer requirements.

## Prerequisites

- Experience using Claude Code to build features (from 01.03)
- Understanding that LLMs can explore codebases (from 01.02)
- Familiarity with the basic constraint that Claude Code has permission modes (from 01.01)

## In Scope

- **What plan mode is**: The specific restrictions it places (no file editing, no command execution, no test running) and what it _allows_ (reading, exploring, analyzing)
- **Why it solves the hallucination problem**: The specific failure mode students just experienced (agent inventing solutions instead of learning patterns) and how exploration-first fixes it
- **The psychological benefit to the developer**: How iterating on requirements with the agent _before_ coding forces clarity on what you actually want (decision-tree metaphor)
- **The practical loop**: 1) State what you want, 2) Enter plan mode, 3) Iterate with the agent, 4) Exit and execute
- **When you're done iterating**: The feeling of "shared understanding" — the agent has asked the right questions, you both know what to build
- **Why even small bug fixes benefit from plan mode**: 2-minute exploration catches bugs that aren't actually one-liners
- **Context window priming**: Why _not_ clearing context between planning and execution leads to better code (the agent keeps loaded context about patterns and decisions)

## Out of Scope

- **How to set up plan mode technically** (command flags, `/plan` syntax) — covered in 01.06
- **AGENTS.md configuration** — covered in Day 2 (02.01-02.02)
- **Dictation tools and workflow optimization** — mentioned in article but detailed setup is future
- **Multi-phase plans for massive tasks** — covered in Day 3 (03.03)
- **Actual hands-on practice with plan mode** — covered in 01.06

## Teaching Sequence

1. **Start with the failure state** — Students just tried building a feature without plan mode. Acknowledge what probably went wrong: the agent hallucinated solutions instead of learning the codebase. This is the pain point plan mode solves.

2. **Define plan mode concretely** — Show the permission table. What's blocked? (File editing, command execution, tests.) What's allowed? (Reading, exploring, analyzing.) Make it clear this is a _constraint that forces focus_.

3. **Explain the exploration-first payoff** — When the agent can't write files, it focuses entirely on understanding. By the time you exit plan mode, its context window is fully loaded with your patterns, your file structure, your conventions.

4. **Walk the decision-tree metaphor** — Use the house-building example (size → stories → stair placement → materials → cupboard). Show that iterating on requirements isn't wasted time — it's you and the agent walking a design tree together, clarifying what you both want.

5. **Address the "is this slower?" question** — Yes, sometimes. But the payoff is in code quality and extending your reach into unfamiliar codebases. You're not just coding faster — you're learning, building intuition, and reducing mental fatigue.

6. **End with the shared-understanding anchor** — When you know the agent has asked all the right questions and you both understand what to build, you can delegate with confidence.

---

**Note on delivery**: The article exists; this lesson should follow it closely but in conversational form. Use the interview transcript as a guide — the instructor's framing around "I was a skeptic," the emphasis on shared understanding, and the decision-tree analogy are the emotional/conceptual core.

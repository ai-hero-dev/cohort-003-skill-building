# Scoping Document: What Are Agent Skills?

## Scope

Skills are reusable, progressively-disclosed instruction sets that solve the agents.md bloat problem and distribute easily across teams and organizations. This lesson explains the concept and value proposition—not how to build one.

## Prerequisites

- Completed Lesson 02.01: What Is an agents.md File? (understand that agents.md exists and what it contains)
- Completed Lesson 02.02: Steering an Agent with the agents.md File (understand how to write directives in agents.md)
- Practical experience that agents.md files can grow large and unwieldy

## In Scope

- The problem skills solve: agents.md files create cognitive overload for the LLM as they grow
- How progressive disclosure works: agent sees only skill name + description in agents.md; full instruction loads only on invocation
- Two invocation patterns:
  - Agent-invoked (agent decides it needs a skill to complete its task)
  - User-invoked (human explicitly triggers a skill to change agent behavior—e.g., "write a PRD," "plan a refactor," "run TDD")
- Distribution benefit: skills as portable, shareable folder structures across teams and open-source ecosystems
- One concrete example: simple skill.md format shown (just enough to demystify the structure, not teach building)

## Out of Scope

- How to build or create a skill (covered in Lesson 03.04: A Skill for Writing Skills)
- MCPs (Model Context Protocols) or underlying technical infrastructure
- Hands-on skill creation or exercises
- Advanced skill patterns, nested progressive disclosure, or skill composition
- Implementation details of how Claude Code loads or caches skills

## Teaching Sequence

1. **The pain point** — show why large agents.md files become a problem (cognitive load on the LLM, every invocation has to parse everything)
2. **Skills as the solution** — introduce the core idea: reusable instruction sets with lazy loading
3. **Progressive disclosure mechanics** — explain why this works: agent only sees name + description until it invokes the skill
4. **Two invocation patterns** — distinguish when an agent would self-invoke vs. when a human would invoke (with brief, relatable examples: agent decides "I need the validation skill" vs. human says "use the TDD skill to guide your approach")
5. **The distribution angle** — skills as portable, shareable artifacts across teams and open source (skills.sh reference optional)
6. **One concrete example** — show a simple skill.md structure to demystify the format (optionally reuse a concept from Lesson 02.02 if continuity helps, but keep it simple)
7. **Close with a bridge** — "Next lesson, you'll use a skill-writing skill to build your own"

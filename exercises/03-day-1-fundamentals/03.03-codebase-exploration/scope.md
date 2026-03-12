# Scoping Document: Codebase Exploration

## Scope

Learn why codebase exploration is the foundational skill for AI coding agents, and practice using agents to understand unfamiliar codebases by mapping architecture, identifying tech stacks, and answering domain-specific questions (like determining which React Router mode a project uses).

## Prerequisites

- Completed lesson 01.01 (The Constraints of LLMs) — understands that LLMs are stateless and start each session from zero
- Basic familiarity with file systems and code navigation
- Understanding that agents can search the web, not just local code

## In Scope

- **Why exploration is foundational:** Every agent session begins with exploring the codebase because agents have no memory between interactions
- **How agents explore like humans do:** File system navigation (tree commands), reading key files, using file naming and structure as signals
- **What good exploration looks like:** Tech stack identification, key file discovery, project purpose understanding
- **Combining local + external context:** Using agents to research external documentation (e.g., React Router modes) alongside codebase analysis
- **Understanding the specific codebase:** Exploring the course project to determine its tech stack and architectural choices (e.g., which React Router mode it uses)
- **How file structure and naming matter:** Poor organization creates the same obstacles for agents as for humans

## Out of Scope

- Deep dives into React Router internals (that's domain knowledge; focus on exploration method)
- User roles and permissions implementation details (save for lesson 01.03 when building features)
- How to steer agents with agents.md files (covered in Day 2)
- Multi-phase exploration or splitting exploration across contexts (covered in Day 3)
- Testing, feedback loops, or autonomous execution (Days 4–5)

## Teaching Sequence

1. **The statelessness problem** — establish why agents need exploration every session, not just once
2. **How agents navigate like humans** — file structure → key files → understanding
3. **The exploration workflow** — tech stack → main files → project purpose (starting point for students)
4. **Applying exploration to the course codebase** — students use agents to map the actual project
5. **Leveling up: combining codebase + web research** — show how agents can answer questions that require both (e.g., "What React Router mode are we using?")

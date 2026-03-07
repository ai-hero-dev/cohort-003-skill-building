# Scoping Document: What Are Subagents?

## Scope
Subagents are the mechanism Claude Code uses to work around LLM context window constraints by spawning isolated context instances to handle focused tasks. This lesson builds the mental model that learners will see in action immediately after.

## Prerequisites
- Understanding of LLM context window constraints (02.01: The Constraints of LLMs)
- Basic familiarity with Claude Code workflow (Section 01: Getting to Know Claude Code)

## In Scope
- The problem subagents solve: context window limitations when handling large codebases + multiple tasks
- What a subagent is: an isolated context window instance spawned by the parent agent
- How they work: parent spawns subagent → subagent receives task-specific instructions → works in isolation → reports results back to parent
- Why they matter: enables Claude Code to tackle work that wouldn't fit in a single context window

## Out of Scope
- How to write or request subagents (covered in 02.04: Build a Feature)
- Parallelization and multi-subagent coordination (covered in 02.03: Codebase Exploration and Section 04: Planning)
- Exact instructions Claude Code generates under the hood (covered in 03.01–03.02: agents.md steering)
- Implementation details or technical architecture of subagent creation
- Concrete examples of subagents in action (will see live in 02.03)

## Teaching Sequence
1. **Refresh the constraint** — Remind learner of context window limits from 02.01; establish why a single context isn't enough for real work
2. **Introduce the solution** — Explain that Claude Code spawns subagents: separate instances with their own context windows
3. **Explain the mechanism** — Walk through the flow: spawn → receive task-specific instructions → work in isolation → report back to parent
4. **Signal what's next** — "In 02.03, you'll see this in action when Claude Code explores a real codebase"

---
# Scoping Document: Managing Your Claude Code Session

## Scope
Teach learners how to navigate Claude Code's core interface mechanics—sending prompts, monitoring session activity with built-in commands, interrupting execution, and clearing session history—so they can operate the tool confidently before learning *when* and *how* to use it strategically.

## Prerequisites
- Claude Code is installed and can be opened
- Learner is familiar with a project repository (from prerequisite orientation section, not in course structure)
- Learner has a Claude account with API access

## In Scope
- How to send a prompt in Claude Code and receive a response
- The `/usage` command: what it displays and how to interpret it
- The `/context` command: what it displays and how to interpret it  
- How to interrupt Claude mid-execution
- The `/clear` command: what it does and how to verify the reset
- All mechanics demonstrated hands-on in a live Claude Code session

## Out of Scope
- *Why* you monitor context or usage (covered in 02.01: The Constraints of LLMs)
- *When* you should clear your context (session strategy in future lessons)
- *How* to prompt effectively (covered in 01.02: Prompting in the Terminal)
- What context windows are or why they matter (covered in 02.01)
- Permissions or security implications (covered in 01.05: Permissions)

## Teaching Sequence
1. **Send your first prompt** — Ask "Which package manager am I using?" so learner sees Claude answering a real question about their project and becomes comfortable with the send/receive loop.
2. **Check `/usage`** — Run the command to show what session consumption looks like after one prompt (observation only).
3. **Check `/context`** — Run the command to show what Claude is currently holding in session memory (observation only).
4. **Interrupt a long task** — Send a time-consuming prompt (e.g., "analyze the structure of this codebase in detail"), then interrupt it mid-execution so learner experiences the interrupt mechanic concretely.
5. **Clear and verify the reset** — Run `/clear`, then `/context` again to show the session memory has been wiped—this makes the reset visible and concrete.
6. **Send a final prompt** — Confirm the session works normally after clearing, providing closure and a sense of completion.
# Scoping Document: Running Bash Commands in Claude Code

## Scope
Learn three ergonomic patterns for executing bash commands while working with Claude Code — `!` prefix, backgrounding with `&`, and Ctrl+Z suspension — so you can choose the right interaction mode for your situation.

## Prerequisites
- How to start and manage Claude Code sessions (02.01)
- How to prompt Claude in the terminal (02.02)
- Understanding of Claude Code's constraints on what it can execute (02.06)
- Basic familiarity with bash command syntax (no deep expertise needed)

## In Scope
- **`!command` syntax** — Explicitly telling Claude to execute a specific bash command; how Claude automatically incorporates the output into its context
- **Backgrounding with `&`** — Running long-running processes (dev servers, etc.) in the background so the terminal stays available; how Claude tracks backgrounded processes
- **Ctrl+Z suspension** — Pausing Claude to take full terminal control, then resuming; understanding what persists and what doesn't
- **Decision tree** — When to use each pattern based on your task (exploratory commands vs. dev servers vs. needing full control)

## Out of Scope
- Deep bash or process management theory (assume learners pick up bash as they go)
- The permission/constraint system itself (that's 02.06's job; this lesson shows *alternatives*, not workarounds)
- Advanced terminal debugging or sophisticated process management
- What happens when backgrounded processes encounter errors or require input
- Terminal state persistence and recovery strategies (too detailed for this lesson)

## Teaching Sequence
1. **Intro: Three patterns for bash interaction** — Acknowledge that Claude Code has ways to execute commands; show there's more than one approach depending on context
2. **The `!` prefix** — Start with the simplest, most direct method; show Claude executing, seeing output, incorporating it into context (example: running a test or checking a file)
3. **Backgrounding with `&`** — When you need a process running but need the terminal free; brief explanation of what `&` does, why you'd use it (running a dev server), how Claude knows about it
4. **Ctrl+Z suspension** — When you need complete control; how to suspend and resume, what this is useful for (full terminal takeover), what terminal state doesn't persist
5. **Decision scenarios** — Three concrete situations showing which pattern to pick (quick command check → `!`; long dev server → `&`; need to run multiple commands as you → Ctrl+Z)

---
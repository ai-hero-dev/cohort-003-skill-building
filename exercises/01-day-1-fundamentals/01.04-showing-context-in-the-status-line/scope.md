# Scoping Document: Showing Context in the Status Line

## Scope
Show learners how to install and configure a tool that displays their Claude Code context window usage percentage in their status line, so they can monitor context consumption in real-time and stay below the 40% degradation threshold.

## Prerequisites
- Familiarity with Claude Code (from 01.01–01.03)
- Basic comfort with command-line tools and file configuration
- Understanding that context window management is critical for AI coding quality (covered in 01.01)

## In Scope
- Why real-time context visibility matters (the "healthy paranoia" angle—40% is the degradation threshold)
- Installing `ccstatusline` globally via npm
- Configuring `ccstatusline` with a minimal settings.json file
- Setting up a wrapper script to pipe context percentage into Claude Code's status line
- Making scripts executable and updating Claude Code settings
- Verification that the percentage appears in the status line

## Out of Scope
- Git status information (repo name, branch, file counts) — save fancy status line customization for a future lesson if needed
- What to *do* when you hit 40% context (context clearing strategies, session management, etc.) — covered in 01.06 (plan-execute-clear loop) and beyond
- Alternative tools or deeper explanations of how ccstatusline works under the hood
- Docker or sandboxing setup

## Teaching Sequence
1. **Brief motivation** — context paranoia is constant; 40% is the dumb zone; Claude Code doesn't show it by default; you need it visible *while you're coding*
2. **Install ccstatusline** — one npm command, global install
3. **Create the config file** — minimal .json with context-percentage setting, explain the key setting (`"rawValue": true` to show just the number)
4. **Create the wrapper script** — simple bash script that pipes input to ccstatusline
5. **Make executable and update Claude Code settings** — final two steps to wire it up
6. **Quick verification** — confirm the percentage appears in the status line and celebrate the win

---

**Note:** The learner should feel *done* after this lesson. They walk away with a working status line and are ready to use it as feedback in 01.05 and beyond. No loose threads.
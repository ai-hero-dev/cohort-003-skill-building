A: The idea of this lesson is I want to explain what sub-agents are in that they are a context-saving mechanism for Claude Code to basically allow it to run tasks. The sub-agent then does some tasks in its own isolated context window, then reports back to the parent agent. I also want to talk about then being able to run in parallel. This will be a knowledge-based exercise and I'll probably just run through examples on the screen.

Q: Great — I can see where this sits in the course, and I have some immediate thoughts.

**First, the positioning**: This lesson comes right after "The Constraints of LLMs" (02.01) and before "Codebase Exploration" (02.03). That's *perfect* context. The learner just learned that LLMs have limited context windows — now you're showing them the practical mechanism Claude Code uses to work around that constraint. Then immediately after, they explore a real codebase. This is a tight, logical sequence.

**But I need to push back on scope.** You've listed three things:
1. What subagents are (the concept)
2. How they save context (the mechanism)
3. How they run in parallel (the scaling behavior)

Here's my concern: **#3 feels like it belongs in a different lesson.** Parallelization is a scaling/optimization concern that's separate from understanding *what* a subagent is and *why* it exists. 

Right now, the course goes: constraints → subagents → codebase exploration → build a feature → plan mode → plan/execute loop. Parallelization feels like it should come *later*, maybe alongside the planning lessons (04.xx), when the learner is tackling *massive tasks* that would benefit from parallel work.

**So here's my question**: Are you planning to teach parallelization because it's fundamental to understanding how subagents work (i.e., the learner can't understand subagents without knowing they're parallel)? Or are you teaching it because it's a cool feature of subagents that will be useful later?

If it's the latter, I'd **cut it from this lesson** and leave it for when you cover task distribution and multi-phase planning. If it's the former, help me understand why — what does the learner need to know about parallelization *right now* to grasp subagents?

A: Yeah I guess we can show that in the exploration lesson probably.

Q: Perfect — **that's the right call.** Parallelization can live in 02.03 (Codebase Exploration) or even later when they're actually *using* subagents to do meaningful work. Right now, the learner just needs to understand the mechanism.

So we're down to **two core pieces**:
1. What subagents are (the concept/definition)
2. How they work as a context-saving mechanism (the *why* and *how*)

Now I need to nail down the actual takeaway. Here's my test question:

**After this lesson, what should the learner be able to do?**

Is it:
- **A)** "Explain to someone else what a subagent is and why Claude Code uses them"
- **B)** "Recognize when Claude Code is spawning a subagent and understand what's happening under the hood"
- **C)** "Request or write prompts that deliberately use subagents to solve a problem"

My instinct is it's closer to **(A + B)** — you're building mental models, not teaching them to *use* subagents yet. That's more of a 02.04 (Build a Feature) thing once they see it in practice.

Am I reading that right? And if so, for a knowledge-based lesson with screen examples, how deep do you want to go? Should we explain:
- The basic concept (what gets spawned, what context it gets, what it reports back)?
- The mechanics (how the parent agent knows when to spawn one, how results flow back)?
- Or just the concept + one or two concrete examples?

What's your instinct on density here?

A: Yeah it's A and B here. We're not necessarily trying to use sub-agents. We're just trying to focus on what they do.

Q: Excellent — that's **clean scope**. We're building mental models, not teaching hands-on usage yet.

Now I want to probe the **teaching sequence** because this is where knowledge-based lessons often stumble.

Here's how I'd instinctively structure it, but push back if this doesn't feel right:

1. **Start with the problem** — Remind them briefly of what they just learned: LLMs have finite context windows. Show a concrete example: "If Claude Code needs to explore a 50,000-line codebase AND write a feature AND run tests, that won't fit in one context window."

2. **Introduce the solution** — "Claude Code solves this by spawning a subagent: a separate instance with its own context window that handles one focused task."

3. **Show what happens** — Walk through the flow: Parent asks subagent to do X → Subagent gets Y context (code snippet, instructions, tools) → Subagent works in isolation → Reports back to parent with results. Maybe use a diagram here.

4. **Show concrete examples** — "Here's what it looks like when Claude Code actually does this" (screen recording or live demo).

The question is: **Should we show the examples at the end (as confirmation) or weave them throughout (as the teaching device)?**

For a knowledge lesson, I lean toward: concept first (so the learner has the frame), *then* examples (so they can recognize what they're seeing).

Does that sequence feel right to you, or would you structure it differently?

A: I think maybe we don't even need the concrete example to be honest, just because we're going right into a concrete example next by initiating an explore sub-agent.

Q: **Perfect call.** You're absolutely right — the next lesson (02.03) is literally "Codebase Exploration," which will involve *watching* a subagent in action. There's no point in rehearsing the example here when they'll see it live immediately after.

So we strip it down to **pure concept + mechanism**:

1. **The problem** — Context window constraints (just refresh from 02.01)
2. **The solution** — What a subagent is and how it works (spawn → isolated context → report back)
3. **Why it matters** — The learner now understands the *mechanism* they're about to see in action

This is actually **stronger** pedagogically. You're not over-explaining. You're giving them the frame so that when they hit 02.03 and Claude Code spawns an explore subagent, they go "Oh, *that's* what's happening" instead of "Where did this come from?"

One last question before we lock scope: **How much detail on the "what context does it get?"** part?

Do we need to explain:
- The subagent gets a copy of the parent's context + specific instructions?
- The subagent has access to the same tools as the parent?
- Something else?

Or is that level of detail premature and we just say "it gets its own isolated context window to work in"?

What feels right for someone who's about to see it in action?

A: It gets specific instructions. It's not always exposed to the user what instructions the sub-agent gets but it's clear that it gets some specific instructions on how to complete the task.

Q: **Got it — that's the right level of detail.** The learner doesn't need to know *exactly* what instructions Claude Code generates under the hood, but they should understand that the subagent isn't just a blank slate — it gets **task-specific guidance** to focus on one job.

This also naturally connects to 03.01-03.02 (agents.md and steering), where they'll learn how to *explicitly control* what instructions agents get. So you're planting a seed here without over-explaining.

Okay, I think we have enough to lock this down. Let me propose the structure:

---

**Scope Summary**

**Lesson title**: What Are Subagents?

**Core takeaway**: Subagents are isolated context windows that Claude Code spawns to handle focused tasks when the parent context is too constrained, receive specific instructions for that task, and report results back to the parent.

**Prerequisites**: 
- Understanding of LLM context window constraints (from 02.01)
- Basic familiarity with how Claude Code works (from section 01)

**In scope**:
- The problem subagents solve (context window constraints)
- What a subagent is (isolated context instance)
- How they work (spawn → receive task-specific instructions → report back)
- Why they matter for Claude Code's workflow

**Out of scope**:
- How to write or request subagents (comes in 02.04 and beyond)
- Parallelization and multi-subagent coordination (comes in codebase exploration and planning lessons)
- The exact instructions Claude Code generates (comes in 03.01-03.02 when discussing agents.md)
- Implementation details of how subagents are technically created

**Teaching sequence**:
1. **Refresh the constraint** — LLMs have finite context windows; recall the problem from 02.01
2. **Introduce the mechanism** — Claude Code solves this by spawning subagents (separate instances)
3. **Explain the flow** — Subagent receives task-specific instructions → works in isolation → reports back to parent
4. **Signal what's next** — "In 02.03, you'll see this in action when we explore a codebase"

---

Does that land? Anything you'd adjust?
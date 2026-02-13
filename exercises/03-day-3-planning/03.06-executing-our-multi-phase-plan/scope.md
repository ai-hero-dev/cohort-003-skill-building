A: Okay at this point they have a PRD and a multi-phase plan that's been written with Tracer Bullets. This exercise is basically a playground for them to actually execute the plan and go ahead with it.

Q: Okay, I'm getting a clearer picture. Let me ground this in the course structure:

They're coming out of **03.05 - Use Tracer Bullets in our Multi-Phase Plan**, where they've built a concrete, phased plan with tracer bullets as proof-of-concept. Now they're moving into **03.06 - Executing Our Multi-Phase Plan** before the course pivots to **feedback loops in Day 4**.

Here's my immediate read: **This lesson sits at a dangerous junction.** It's a transition from planning to doing, which means it could easily become "here's everything you need to know to execute any multi-phase plan" — which would swallow up half of Day 4's feedback loop material.

So let me push back and ask some clarifying questions:

1. **What is the learner's actual constraint in this lesson?** Are they just... executing the plan they built? Or is there a *specific insight* about execution you want to land? (For example: "How to handle mid-execution plan adjustments" or "How to know when to stop and replan" or "How to communicate progress back to the plan"?)

2. **Is this a *sandbox exercise* where they just go build the thing?** Or do you want them to practice something specific about the *execution pattern itself*?

3. **What should break or go wrong?** The best learning happens when they hit a real constraint. Should they discover that one phase is harder than expected? That the plan was wrong? That they need to adjust mid-phase?

4. **How does this connect to Day 4?** If Day 4 is all about feedback loops and quality, what should they *not* worry about optimizing here?

What's the core insight you're trying to land in this lesson?

A: Yeah this is a sandbox exercise but I think also it's a way of: this is the first time they've actually executed a multi-phase plan at all. They should be using the Tracer bullets approach to basically say, 'Okay during that phase provide feedback on what was built.' I guess there are angles here where we can talk about integrating that back into the plan somehow, sort of improving the plan as we go. I'm not sure what you think about that.

Q: Okay, now we're getting somewhere. But I need to push back a bit, because I'm seeing **two different lessons** trying to happen here:

**Lesson A**: "Execute your multi-phase plan by actually building the tracer bullets phase-by-phase, and after each phase, pause to see what you built."

**Lesson B**: "Use feedback from each phase to iteratively improve your plan as you go."

These feel like they belong in different lessons to me. Here's why:

- **Lesson A** is about the *discipline* of stopping after each phase and assessing. That's a behavioral/procedural thing. The learner needs to experience: "I built phase 1, I looked at it, it works, I move to phase 2."
- **Lesson B** is about the *feedback loop* — taking what you learned and actually *changing the plan*. That's a meta-level skill and it feels philosophically closer to what Day 4 is about.

So here's my question: **What do you want them to actually experience in THIS lesson?**

Is it:
- **Just the execution discipline?** ("Build phase 1, review what you built, move to phase 2, repeat") — *stop there, don't touch the plan yet*
- **Or the full loop including plan refinement?** ("Build phase 1, review it, adjust your understanding of phase 2 based on what you learned, execute phase 2")

Because if it's the second one, you're stepping on Day 4's toes. Feedback loops are a big deal in this course — they get their own day. I'd rather see this lesson be lean and focused on **just executing the plan as written**, and then *in Day 4* you introduce the idea of "feedback should inform your next iteration of the plan."

What's your instinct?

A: I think probably just the execution discipline. That's what we want from this lesson. We want to simply execute the plan, also I think a big part of this is understanding that you should clear the context at the end of each phase of the plan they've not actually done. Giving that a go, understanding discipline around context during executing a plan is really important so I think yeah, we plan refinement is probably not on the table.

Q: Perfect. **That's a much tighter scope, and I like it.** You're landing on something really concrete: the learner needs to experience the *rhythm* of multi-phase execution — build, review, **clear context, move on**.

This is actually critical because they've learned about context management in isolation (01.04, 01.06), but they haven't *felt* the pressure of it during a real multi-phase effort. That's the insight here.

So let me reflect back what I'm hearing:

**Core takeaway**: When executing a multi-phase plan, you build one phase completely, review what you built, intentionally clear the context window, and move into the next phase fresh — and that discipline is what keeps you from getting lost across multiple phases.

That's **one clear thing**. No plan refinement, no meta-loops, no "improving as you go." Just: **execute phase 1 → review → clear → execute phase 2 → repeat**.

A couple of quick follow-ups before I write the scope summary:

1. **How explicit should the "review" step be?** Should they articulate what worked/what didn't? Or just "look at what you built"?

2. **When they clear context, are they clearing it in Claude Code itself?** (Like, closing the conversation and starting fresh?) Or is this more conceptual?

3. **Should they hit any friction here?** Like, should the experience of clearing context actually be *uncomfortable* enough that they feel why it matters?

A: They're reviewing it back to the agent, right? You can think of each phase of the plan as:
1. An explore phase where the agent explores the code base and understands what it needs for that specific phase.
2. The implementation.
3. The user feedback and testing. The user feedback and testing should be like, "That's gonna burn some context, right?" By the end of it you might be pushing into the dumb zone of the LLM so you need to be really cautious about that.
The loop is really like:
1. You should really just be able to prompt the LLM with the PRD and the plan and then say, "Do phase one."
2. Then you let it get on with its implementation.
3. Then you review its implementation. You give feedback to the LLM in the same context window.
4. Then once you're happy with phase one you clear it. Prompt it again with the plan and the PRD in phase two and you repeat.

Q: Ah, **now this is crystalline.** And I see it clearly — each phase is its own mini-context-budget cycle. That's smart.

But I want to make sure we're scoping this right, because I'm seeing a potential trap:

**The lesson could accidentally become a tutorial on "how to give good feedback to Claude"** — like, teaching them feedback techniques, iteration strategies, when to ask for revisions vs. rewrites, etc. That's *valuable*, but it's also **Day 4 territory** (red-green-refactor, feedback loops).

So here's my boundary check: **In this lesson, are they learning:**

- **A**: The *structure* of multi-phase execution (explore → implement → review → clear → repeat with fresh context)?
- **B**: The *skill* of giving effective feedback during the review step?

I think this lesson should be **almost entirely A**. The review step happens, they give feedback, Claude iterates — but this lesson isn't about *teaching them to be good at feedback*. They're just experiencing the rhythm and the context management discipline.

**Does that match your thinking?** Or do you think they need to actually get good at the feedback part too in this lesson?

And one more practical question: **How do you want them to trigger each phase?** Do they literally:
1. Paste the PRD + plan
2. Say "Execute phase 1"
3. Let Claude go
4. Review the output
5. Give feedback in the same window
6. Once satisfied, manually clear and start phase 2?

Or is there tooling/automation that helps with this rhythm?

A: So I'd say day four is actually about automated feedback loops. This is really about QAing and providing prompting Claude to hook a job, basically. Like day four is all about optimizing for unit testing, for types, for precommit hooks, et cetera so they are slightly different.

Q: **Ah, that's the distinction I was missing.** Thank you.

So:
- **This lesson (03.06)**: Manual QA discipline. You (the human) are the feedback loop. You review, you prompt Claude to fix things, you iterate until you're satisfied, then you move on. It's about building the *habit* and *discipline* of stopping, reviewing, clearing.
- **Day 4**: Automated feedback loops. Tests, type checkers, linters — the *machine* is giving the feedback, not you.

That clarifies everything. This lesson is about **the human-in-the-loop execution rhythm**, not about becoming a great code reviewer. They just need to feel the discipline: explore → implement → you QA it → you give feedback → Claude fixes → repeat → clear → next phase.

Okay, I think I have enough. Let me write the scope summary:

---

**Scope Summary**

**Lesson title**: Executing a Multi-Phase Plan with Manual QA and Context Discipline

**Core takeaway**: When executing a multi-phase plan, you maintain discipline by reviewing each phase, giving feedback to Claude in the same context window, and then **intentionally clearing the context before moving to the next phase** — this prevents context degradation across multiple phases.

**Prerequisites**: 
- They've built a PRD and a multi-phase plan with tracer bullets (03.05)
- They understand context management and the "plan-execute-clear" loop (01.06)
- They can use Claude Code to execute code (01.03)

**In scope**:
- Executing phase 1 by prompting with the PRD + plan together
- Letting Claude explore the codebase and implement the phase
- Reviewing the output and giving manual feedback in the same context window
- Iterating on feedback until satisfied
- Intentionally clearing the context window and starting fresh for phase 2
- Repeating the cycle for all phases in the plan
- Experiencing the rhythm and discipline of this loop

**Out of scope**:
- Teaching techniques for *excellent* code review or feedback (that's Day 4's domain with automated feedback)
- Plan refinement or iteration based on what they learn (Day 4's feedback loops)
- Automated testing, type checking, or pre-commit hooks (Day 4)
- Optimizing the feedback process itself

**Rough flow**:
1. Set up: remind them they have a PRD and multi-phase plan ready to execute
2. Execute phase 1: prompt Claude with PRD + plan, ask for phase 1 execution, observe the explore-implement cycle
3. Review and QA: manually test/review what was built
4. Iterate with feedback: give Claude feedback in the same context, let it refine until you're happy
5. Clear context: intentionally clear the conversation and note why this matters (context budget)
6. Execute phase 2+: repeat the cycle, emphasizing the fresh-start feeling and why that's valuable
7. Reflection: notice how much cleaner each phase feels with a fresh context window

---

Does that land? Anything you'd adjust?
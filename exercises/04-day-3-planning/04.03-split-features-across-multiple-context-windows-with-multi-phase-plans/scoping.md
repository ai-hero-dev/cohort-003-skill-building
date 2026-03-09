A: So in this one I think I need to put together an agent skill which takes the PRD that they will have created in the previous exercise and then helps to turn it into a multi-phase plan. Maybe not. I think the student themselves should prompt the Claude Code to say, "Okay take this, turn it into a multi-phase plan," and we won't be executing the fact the plan in this lesson. We're just gonna be looking through the plan, seeing what it creates. And sort of naturally seeing what the Claude Code harness actually does in terms of thinking about plans and multi-phase plans. The whole structure of this section has been set up with the idea that large tasks are hard by default with Claude Code.
1. Then go in and show how to create a PRD to capture lots of information about a large task.
2. Then this is going to be splitting it into a multi-phase plan to actually go and execute it.
3. Then the next one is using tracer bullets to take that and basically make the multi-phase plans better.
4. Then we should probably have space on the end to actually execute the plan.

Q: Okay, I'm getting a clearer picture now. Let me reflect back what I'm hearing, because I think there's a **scope question that needs to be resolved upfront**.

You've got a three-lesson arc in Day 3 (Planning):
1. **03.01** - How to tackle massive tasks (the problem statement)
2. **03.02** - Write great PRDs with this skill (creating structured input)
3. **03.03** - Split features across multiple context windows with multi-phase plans (this lesson)
4. **03.04** - Tracer bullets (refining the plan)

Then presumably Day 4+ executes on that plan.

Here's what I'm hearing about **03.03**:
- The learner takes the PRD they built in 03.02
- They ask Claude Code (in the UI, not via a custom skill) to turn it into a multi-phase plan
- They **observe and understand what Claude Code produces** — not execute it yet
- They learn to read/evaluate/understand the structure of a multi-phase plan
- There's no custom agent skill here; this is just Claude Code doing its natural thing

**My first push-back question:** What's the actual **takeaway** here? Is it:

A) "I can recognize a well-structured multi-phase plan when Claude Code creates one" (read/critique skill)

B) "I understand the principles of how to break a feature across context windows" (conceptual understanding)

C) "I know how to prompt Claude Code to create a multi-phase plan and what parameters/constraints matter" (prompting technique)

These are fundamentally different lessons, and I suspect you're mixing them. If it's (A), this is short and focused. If it's (B) or (C), we need to be clear about what the learner is actually doing and learning.

Which one resonates?

A: Yeah I can recognize a well-structured multiphase plan when Claude Code creates one and yeah so this is a practical exercise A, B, and C probably.

Q: Okay, so you want **all three** — but here's where I need to push back: that's actually **two lessons hiding in one**.

Let me separate them:

**Lesson A (Recognition/Critique):** "I can look at a multi-phase plan and understand why it's well-structured — what makes phases good, how they map to context windows, where Claude Code got it right or wrong."

**Lesson B+C (Prompting/Principles):** "I understand the underlying principles of context windows and phase boundaries, AND I know what prompt/constraints make Claude Code generate good multi-phase plans."

Here's the problem: **A is about reading and evaluating.** You show Claude Code's output, you pick it apart together, you build intuition about what's good. The learner finishes thinking: "I can spot a good plan."

**B+C is about understanding the *why* underneath.** It requires teaching the smart zone/dumb zone concept, context window limits, phase boundaries, dependencies — this is more theoretical scaffolding before you even show a plan.

**My claim:** If you lead with B+C (the principles), then show the plan, then critique it — you'll overwhelm them. They need to **see a plan first**, notice things about it intuitively, *then* learn why those things matter.

So here's my suggestion: **Split this into two lessons.**

- **03.03:** "Recognize a well-structured multi-phase plan" — show output, critique together, build pattern recognition. Light on theory.
- **03.03b (or fold into 03.04?):** "Understand context windows and phase boundaries" — now teach the principles that make good plans. Heavier on conceptual depth.

Does that feel right, or are you genuinely trying to do all three in one go? If it's the latter, I need to see your outline before I believe it's not scope creep.

A: Yeah but B and C are the principles we've already done. In Day one they've had a look at plan mode. We're just tackling the narrow scope of how you would approach building large features with an agent.

Q: Ah — **that changes everything.** Thank you for that context.

So they've already got:
- **01.05** - What is plan mode (the mechanic)
- **01.06** - The plan-execute-clear loop (the rhythm)

And now in Day 3, the focus is specifically: **"How do I use planning strategically when I'm building something genuinely large?"**

That's a much tighter scope. You're not re-teaching plan mode or context windows — you're showing them **how to apply it to real, messy, big features.**

So **03.03** becomes: Given a solid PRD from the previous lesson, show them what Claude Code produces when you ask it to split a big feature into phases, and teach them to **recognize and critique what a good multi-phase breakdown looks like in practice**.

That's **just A** — recognition and critique.

Here's my actual scoping question then:

**What's the single criterion the learner should use to evaluate whether Claude Code's multi-phase plan is good?** 

Is it:
- "Each phase fits in one context window" 
- "Each phase delivers standalone value / can be reviewed independently"
- "Phases are ordered by dependency"
- "All of the above"

Because that answer will define what you actually show them and what you critique. If it's all of the above, you've got scope creep. If it's one or two, we're locked in.

What's the **one thing** that makes a multi-phase plan *work*?

A: Yeah, task sizing is a key one here. I suppose the lesson here is really not that much in it, right? We're just basically getting them to create a multi-phase plan because in the next lesson we're going to show them how to create a good multi-phase plan. If anything we are looking for a sub-optimal plan here or just a basic plan to see what the LLM, what the agents' natural instincts are and then next we're going to look at improving the plan.

Q: **Ah — now we're talking.** This is actually much simpler than I thought.

So **03.03** is basically: "Here's what Claude Code naturally does when you ask it to split a big feature into phases — let's just observe it, no judgment yet."

And **03.04 (Tracer Bullets)** is: "Now let's make that plan *better* using tracer bullets as a technique."

That's a clean two-lesson arc: **observe → improve.**

So the scope of **03.03** is actually **really narrow**:

1. Learner takes their PRD from 03.02
2. They prompt Claude Code: "Turn this into a multi-phase plan"
3. They see what it produces
4. Maybe you annotate it a bit, name what they're looking at, but **you don't critique it yet**
5. Lesson ends with: "This is what we're starting with; next lesson we make it better"

**Single takeaway:** "I can see what a basic multi-phase plan looks like and understand how Claude Code naturally structures big tasks."

**Prerequisites:** The PRD they built in 03.02, basic understanding of plan mode from Day 1.

**In scope:** Generating and observing a multi-phase plan.

**Out of scope:** Evaluating it, improving it (that's 03.04), executing it (that's later).

Is that right? And if so — **how much do you want them to see?** One example plan? Multiple? Or are you building a skill that generates the plan and they're just prompting Claude Code directly in the UI?

A: Yeah I think they're gonna be creating the plan themselves from the PRD and so we can give them an example prompt, just a single sentence which says, "Okay, here's just tell Claude Co to create a plan." I don't think we're building a skill here. We'll just literally get them to take in the PRD, reference it via @, and then get them to generate a plan based on that.

Q: Perfect. That's **dead simple and focused.**

So the lesson is basically:
1. "Here's an example prompt you can use" (one sentence)
2. "Take your PRD from 03.02, reference it with @, ask Claude Code to create a multi-phase plan"
3. "Look at what you got"
4. Done.

**One final scoping question before I lock this in:**

Do you want them to actually **run this in Claude Code during the lesson** (so they have a real artifact to look at), or are you giving them an *example* of what a multi-phase plan looks like and they just read/understand it?

Because that changes the lesson slightly:

- **If they execute it:** The lesson is interactive, they see their own output, but you need to account for variation in what Claude Code produces.
- **If it's an example:** You control the narrative, it's tighter, but less hands-on.

Which approach fits the vibe of this course? I'm guessing hands-on (they've been building features since Day 1), but I want to check before I write the scope summary.

A: No yeah, it's a skills-based exercise. They'll be running it in Claude Code during the lesson.

Q: Perfect. Then we're locked in.

---

**Scope Summary**

**Lesson title**: Generate a Multi-Phase Plan From Your PRD

**Core takeaway**: I can take a PRD I've written and use Claude Code to generate a multi-phase plan that breaks a large feature into manageable chunks.

**Prerequisites**: 
- Completed 03.02 (have a written PRD)
- Basic familiarity with plan mode from Day 1 (01.05, 01.06)
- Know how to use @ references in Claude Code

**In scope**:
- Providing a simple, one-sentence example prompt for generating a multi-phase plan
- Learner executes the prompt in Claude Code, using their PRD as input via @
- Observing what Claude Code naturally produces — no critique or evaluation yet
- Understanding that a multi-phase plan breaks a big task into phases

**Out of scope**:
- Evaluating whether the plan is good (03.04 does this)
- Teaching task-sizing principles or phase optimization (03.04 does this with tracer bullets)
- Executing the plan (comes later)
- Building a custom agent skill for this (staying in the UI)

**Rough flow**:
1. Recap: You built a PRD in the last lesson. Now we're turning it into a plan.
2. Here's the prompt you'll use (show the example).
3. Go run it in Claude Code — reference your PRD with @.
4. Take a screenshot or note what it produced.
5. Next lesson, we're going to make that plan better.

---

Does that lock it in?
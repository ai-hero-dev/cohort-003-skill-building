A: Okay at this point we have created a PRD and we created a sort of naive plan. I want to treat this lesson as a knowledge-based setup where we just teach people what tracer bullets are conceptually. Very narrowly scoped, tracer bullets come from the pragmatic programmer and essentially it's a way of vertically slicing information or basically building small slices of features end-to-end instead of building features horizontally.

Q: I like this framing. You're treating this as a **pure concept lesson** — not yet applying tracer bullets to the course project, just building the mental model. That's smart scope discipline.

Let me ground this in the course structure to make sure I'm reading it right:

- **03.01** (How to tackle massive tasks) — presumably introduces the *problem* tracer bullets solve
- **03.02** (Write great PRDs) — you've built the artifact (the PRD)
- **03.03** (Split features across multiple context windows) — this sets up *why* you need tracer bullets for multi-phase plans
- **03.04** (this lesson) — **define what tracer bullets are conceptually**
- **03.05** (Use tracer bullets in our multi-phase plan) — *apply* them to the actual project

So this lesson sits in the "build the concept foundation" spot, right before application. That's a strong location for a knowledge-only lesson.

Before I lock scope, one clarifying question: **How much of the "why does horizontal building fail?" story do you want in here?** 

In other words:
- Are you starting by showing the *problem* (the naive plan they built is horizontal-slice thinking) and then revealing tracer bullets as the solution?
- Or are you just defining "here's what a tracer bullet is, here's the vertical-slice mental model" without doing a before/after on their earlier plan?

The first approach would be more motivating but risks bleeding into 03.03's territory. The second is cleaner scope. Which way are you leaning?

A: Yeah we definitely want a lot of that so we're thinking we're showing the problem of what LLMs do by default, I feel, which is do a lot of horizontal building. They don't get feedback early enough and then later we're defining what a tracer bullet is and why it works.

I've also given you an article I've written about the topic.

Q: Perfect. I've read the article, and here's my read on what you've got:

**The good news:** The article is actually *well-scoped* already. It follows exactly the arc you just described:
1. The Problem (LLM sycophancy → horizontal layer building → "slop")
2. The practical consequence (the database service example is perfect)
3. The concept (tracer bullets = vertical slices)
4. Why it works (feedback loops early)
5. The prompt/technique to force the behavior

**But here's where I'm going to push back:** The article currently does too much work that belongs in **03.03** (Split features across multiple context windows). 

Specifically, this section:
> "Move to the next slice in a fresh context window" and the broader framing about "multi-phase plans"

That's 03.03's job. This lesson should answer: *What is a tracer bullet and why does it work?* Not: *How do you use tracer bullets across context windows?*

Here's my proposal for tightening scope:

**What stays:**
- The problem: LLMs build horizontally, don't get feedback early
- The database service example (excellent)
- Definition: tracer bullets = small end-to-end vertical slices
- Why it works: feedback loops validate assumptions early
- The prompt you can use to encourage the behavior

**What goes (or gets minimized):**
- The multi-phase plan framing
- The Ralph loop mention
- The "move to the next slice in a fresh context window" stuff
- The specific issue example (#161) — it's doing too much showing

By cutting that, you land a clean **"here's a concept, here's why it matters, here's how to ask for it"** lesson that sets up 03.05 perfectly.

Does that align with how you're thinking about it? Should this lesson be purely conceptual, or do you want to include the "how to prompt for it" bit as well?

A: Yeah we definitely don't want the "how to prompt for it" bit because we're going to do that in the next lesson. So you're right not everything in the article will come up here; it's more just background stuff.

Q: Perfect. That's the right call. The prompt section is definitely 03.05 territory — that's where you show them how to *operationalize* the concept.

So here's my final read on scope:

**IN this lesson:**
- The problem: LLMs default to horizontal layer building without feedback
- Why that's bad: you end up with massive chunks of untested code (the "slop")
- The database service example (concrete, relatable)
- What a tracer bullet IS: a small vertical slice that touches all layers end-to-end
- Why it works: validates assumptions early, gets feedback loops in place

**OUT of this lesson:**
- How to prompt for tracer bullets (03.05)
- Multi-phase planning with context windows (03.03)
- The Ralph/specific issue example (too applied)
- Implementation details about *using* them in your actual workflow

**The core takeaway:** After this lesson, learners should be able to explain the difference between horizontal-slice thinking and vertical-slice (tracer bullet) thinking, and understand why the latter matters when working with AI.

That's a clean, focused lesson. One more quick question before I write the scope summary:

**How much detail on the "feedback loop" part do you want?** The article touches it lightly. Should you spend time explaining *what* feedback looks like, or is "you validate assumptions early" sufficient at this point? (I'm guessing you dig into it more in 03.05 when they're actually *doing* it.)

A: Yeah just validate assumptions early; that's basically the thing. The idea is we're going to end up with a really nice plan that will have some kind of feedback mechanism built in. Like you should see this at this point, you should see this at this point.

Q: Got it. So the feedback loop is just the *concept* here — "you validate assumptions early" — and the *actual* feedback mechanism design happens in 03.05 when you're building out the multi-phase plan. Clean.

---

**Scope Summary**

**Lesson title**: What Are Tracer Bullets?

**Core takeaway**: Learners understand that tracer bullets are small, end-to-end vertical slices of functionality (not horizontal layers), and why this approach prevents LLMs from building untested code in isolation.

**Prerequisites**: 
- Understanding that LLMs have been used to build features (from 01 and 02)
- Familiarity with the concept of "layers" in software (frontend/backend, API/database, etc.)
- Awareness that naive AI prompts tend to over-deliver and lack feedback (implied from course arc)

**In scope**:
- The problem: LLMs default to horizontal layer building without early feedback
- Why it's bad: massive untested code chunks ("slop"), huge review burden, assumptions validated too late
- The concrete example: building a database service (all endpoints, models, auth, logging first, *then* connecting to DB)
- Definition: tracer bullets = small vertical slices that touch all system layers end-to-end
- Why tracer bullets work: they force early validation of assumptions through feedback loops

**Out of scope**:
- How to prompt for tracer bullets (03.05)
- Multi-phase planning and context window splitting (03.03)
- Specific implementation examples or workflows
- The actual feedback mechanism design (03.05)
- Ralph, agents.md, or tool-specific prompting

**Rough flow**:
1. Open with the problem: what do LLMs naturally do when building features?
2. Show the consequence with the database service example (everything horizontal, connection fails at the end)
3. Introduce the concept: tracer bullets are vertical slices, not horizontal layers
4. Explain why it works: early feedback validates assumptions before you invest in the full build
5. Close with: this is why the next lesson's plan matters

---

Does that lock it for you?
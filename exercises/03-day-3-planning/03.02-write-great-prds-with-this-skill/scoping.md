A: So this is a skills-based lesson. You come into this lesson with a skill that I've written on how to create a PRD and an idea for a feature that I want to help you build, and that's what we're going to do in this lesson: build the PRD for this feature.

In the next exercise after this we take that PRD and turn it into a multi-phase plan, and then we take that multi-phase plan to use tracer bullets to re-execute the plan and re-create the plan. I think maybe in the tracer bullets exercise we actually execute the plan.

Q: Okay, I see the shape of this now. Let me ground my thinking in the course structure first:

**Context**: You're in **Day 3 (Planning)**, and the flow is:
- 03.01: How to tackle massive tasks (conceptual foundation)
- **03.02: Write great PRDs with this skill** (you are here)
- 03.03: Split features across multiple context windows with multi-phase plans
- 03.04: Tracer bullets

So the progression is: **concept → PRD-writing skill in action → breaking PRD into phases → executing with tracer bullets**.

This tells me something important: **03.02 is NOT about building a feature. It's about producing a really good PRD that becomes the input for 03.03.**

---

**Here's my read on the scope, and I want to push back slightly:**

The code stub says:
> "Use the write-a-prd skill to build instructor analytics: Revenue trends, Enrollment, Completion rates, Quiz pass rates, Drop-off points"

But I'm hearing you say: "You come in with a skill, and an idea for a feature, and we build the PRD together."

**These might be two different things.** Let me ask:

1. **Is the "instructor analytics dashboard" the feature idea that learners walk in with?** Or is that an example you're showing?

2. **What does "use the write-a-prd skill" actually mean in practice?** Are learners:
   - Prompting Claude with a template/framework they learned earlier?
   - Following a step-by-step worksheet?
   - Working through the skill interactively with Claude Code?

3. **Most importantly: What's the ONE thing a learner should be able to do after this lesson that they couldn't before?** Is it: "I can take a half-baked feature idea and turn it into a solid PRD that's detailed enough for a multi-phase plan"?

Because if that's the takeaway, then **the instructor analytics example is just the vehicle** — the lesson is really about **the PRD-writing process itself**, not about building analytics specifically.

What am I missing?

A: Yeah by this point they understand how to invoke skills. We're just invoking the writer PRD skill, walking through it and understanding what a PRD kind of contains. They should be able to feel confident using this skill to create PRDs in the future and feel confident scoping down big features into things that you can actually design with. We're also sort of teaching a meta skill here, which is the ability to be clear in your requirements and to understand them fully.

Q: Perfect. Now we're talking about **real scope**.

So the core takeaway is: **After this lesson, learners can use the write-a-prd skill to turn a vague feature idea into a clear, scoped PRD — and they understand why that clarity matters for working with Claude.**

That's tight. That's good.

But I want to make sure we're not doing too much work in one lesson. Let me probe:

**The meta skill angle** — "be clear in your requirements and understand them fully" — is this something you're *teaching* in this lesson, or are learners *discovering* it by doing the exercise?

Because there's a difference:

- **Discovery path**: "Here's a messy feature idea. Let's use the PRD skill. Oh look, the skill forced us to think about X, Y, Z we hadn't considered. Now the idea is clearer."
- **Teaching path**: "Before we use the skill, let me explain why clarity matters, here are common pitfalls, then we use the skill to practice."

I'm guessing you want **discovery** — learners feel the friction of unclear thinking when the skill prompts them, then feel the relief when it's resolved. That's more elegant.

**Second thing**: The instructor analytics feature — is that the *only* example, or do learners bring their own feature idea? Because if it's just an example you walk them through, that's different from them doing the exercise themselves.

**Third**: How much time/detail are we expecting? Is this a "15-minute walkthrough" or a "45-minute deep dive where they really sit with the PRD draft"?

Those answers will tell me if this is scoped right or if it's actually two lessons.

A: Yeah it's a discovery path. This is a skills-based lesson. This is a decent 20-25 minute exercise.

Q: Great. **Discovery path, 20-25 minutes, skills-based.** That's a constraint that actually helps.

One more hard question before I lock scope:

**Do learners use the instructor analytics example, or do they bring their own feature idea?**

This matters because:

- **If it's the analytics example**: You control the complexity, the lesson stays focused, learners see a clean end-to-end walkthrough. Risk: feels a bit scripted.
- **If they bring their own idea**: More authentic, more buy-in, but you lose control over whether their idea is scoped appropriately for a PRD exercise (they might pick something too simple or impossibly complex).

For a **20-25 minute, discovery-based skills lesson**, I'm leaning toward **you providing the feature idea** (instructor analytics) and walking them through the skill together. They learn the *process* by watching it happen on a real example, then they'd have the confidence to do it themselves later.

But here's what I want to confirm: **Is the goal of this lesson to produce a *good* PRD that they'll actually use in 03.03?** Or is the goal just to "understand what a PRD contains and feel confident using the skill"?

Because if it's the former, you need to be more hands-on and iterative. If it's the latter, you can be more exploratory and looser.

Which is it?

A: I think the analytics example is good because they can really choose their own scope there too. It's not exactly a perfectly scoped upfront exercise. It's an idea that can be taken really far or they can just take it a little way. The goal of the lesson is to reach a good PRD.

Q: **Excellent.** That's actually elegant — the feature idea itself has built-in scope flexibility, which mirrors real life.

So to clarify the mechanics: **Learners invoke the write-a-prd skill with the instructor analytics idea, the skill guides them through the thinking, and by the end of 20-25 minutes they have a PRD that's good enough to hand to 03.03 (the multi-phase planning lesson).**

But I need to lock one thing down, because it affects scope:

**How "finished" does this PRD need to be when they leave this lesson?**

- **Scenario A**: They have a solid PRD draft that clearly defines the feature, scoped reasonably, with enough detail that they could actually break it into phases in 03.03. (This is what I'm assuming.)
- **Scenario B**: They have a PRD outline or framework, but it's expected to be refined/iterated in 03.03.

I'm guessing **Scenario A** — because 03.03 is about *splitting the PRD into phases*, not about *finishing* the PRD. The PRD should be done before they get there.

If that's right, here's what worries me slightly: **In 20-25 minutes, can a learner invoke a skill, work through it, iterate if needed, and land on a *good* PRD?**

That's assuming:
- The skill is well-designed and doesn't take forever
- The learner engages seriously (not rushing)
- There's minimal back-and-forth needed

Is that realistic? Or should we be thinking about this as more of a "get a solid first draft" situation?

Because that affects what I'd recommend for the lesson structure.

A: Yeah scenario A. Like the LLM itself, when they're using it, will guide them towards a good PRD. Ideally we do want to create a PRD during this lesson. That's absolutely right.

Q: Perfect. **That's locked: they walk out with a finished, good PRD.**

Okay, last thing before I give you scope, and this is important:

**What should be explicitly OUT of scope here?**

Because I'm thinking about the next lesson (03.03 — multi-phase plans). If learners finish 03.02 with a complete PRD, then 03.03 should assume that PRD exists and just focus on *breaking it into phases*.

So here's what I'd say is **OUT of scope for 03.02**:
- Discussing how to *break the PRD into multiple phases* (that's 03.03's job)
- Actually executing any code or building anything (that comes later in 03.04)
- Deep-diving into the specific analytics metrics or business logic (the skill should keep that lightweight)

But I want to check: **Is the skill itself something they learn in this lesson, or did they learn it in an earlier lesson?**

Because if they're *learning* the skill for the first time here, that's different from *using* a skill they already know. The code stub says "Use the write-a-prd skill" (suggesting they know it), but I want to be sure we're not sneaking skill-teaching into this lesson and calling it an exercise.

What's the actual expectation about what they know walking in?

A: Yeah we will be basically not necessarily learning the skill. It's just a command that you execute. They'll be trying it out here. We're introducing it here for the first time but they won't have seen it. They won't have used it before but they understand the concept of what skills are. They understand the concept that they can invoke skills and I don't think it's that big a leap for them to just start using it straight away.

Q: Got it. **They know skills exist, how to invoke them, but this is their first time using *this specific skill*.** That's totally reasonable — no extra setup needed.

So the lesson is: "Here's a skill that helps you write PRDs. Let's use it on this feature idea and see what happens."

Okay, I think I have enough. One final sanity check on the instructor analytics example itself:

**The five bullet points in the code stub** (Revenue trends, Enrollment, Completion rates, Quiz pass rates, Drop-off points) — are those:
- The *starting point* (a rough list of "analytics we want to track")?
- Or the *end state* of what the PRD should cover?

I'm asking because if it's the starting point, then the skill's job is to turn that vague list into a structured PRD. If it's the end state, we're describing what "done" looks like too early.

My intuition: it's the **starting point** — learners come in with "we want to build an instructor analytics dashboard with these metrics" and the PRD skill turns that into "here's what we're actually building, who it's for, what success looks like, what's in scope, what's not, etc."

Is that right?

A: That's the end state of what the PRD should cover. They don't have to cover all of that but of course within that specification there's a ton of different room for details, right? Sure it seems like it's over specified up front but it really really isn't. There's a lot in there that is under specified and the PRD skill will help flush that out by grilling the user on what they think they should build.

Q: **Perfect.** That actually makes total sense — the five bullet points are the *ambition level* they can aim for, not a checklist. The skill will interrogate what those actually mean, which is exactly the discovery you want.

So learners walk in thinking "we want Revenue trends, Enrollment, Completion rates, Quiz pass rates, Drop-off points" and walk out with a real PRD that clarifies: *Which* users need *which* of those metrics? What's the priority? What's phase 1 vs. phase 2? What counts as done?

That's the meta skill in action — **clarity emerging from rough thinking.**

---

Alright, I'm ready to give you scope. But before I do, one tiny thing:

**What's the structure of the lesson itself?** Is it:
- An explainer that walks them through the skill?
- A prompt/exercise where they invoke the skill themselves?
- A video walkthrough?
- Something else?

Because that changes how I'd advise on the lesson *shape*, not the scope itself, but it's worth knowing.
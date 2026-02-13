A: So at this point they understand what tracer bullets are from the previous exercise and they have a multi-phase plan that they are essentially trying to critique. This should be somewhere on the file system and this plan then, they are going to essentially redo the whole thing from scratch.

They'll look at the PRD that they've created in the previous exercise and instead of prompting just for a sort of naive multi-phase plan, they're going to prompt with tracer bullets in mind. We're going to give them maybe a paragraph of text that they can paste into their prompt and/or maybe even a tracer bullet skill, to be honest. A tracer bullet skill might just be cleaner.

We pull that into the repo then the contextualizes it with the PRD and then creates a beautiful plan that we're not going to execute yet. That's coming in the next exercise but the scope of this one is basically just to see the differences between the plan that the tracer bullets section creates and our naive plan.

Q: Okay, I'm seeing this clearly now. Let me ground my read in the course structure:

**Where this sits**: 
- 03.04 teaches *what* tracer bullets are (concept)
- 03.05 (this lesson) applies that concept to the multi-phase plan they already created
- 03.06 actually executes that improved plan

So this is the **bridge lesson** — the moment where they see tracer bullets make a tangible difference.

**What I'm hearing**:
1. They have a naive multi-phase plan from 03.03
2. They'll re-prompt using a tracer bullet skill (or a provided prompt snippet)
3. They'll get a new, better plan
4. They'll compare the two and observe the differences
5. Importantly: **they don't execute yet** — that's 03.06's job

**My first clarifying question**: 

The core takeaway I'm inferring is: **"You can generate a significantly better multi-phase plan by explicitly asking Claude to think in tracer bullets first."** Is that right? Or is it more nuanced — like, is there a specific *way* to integrate tracer bullets into your prompting that matters?

Also — **should they build the tracer bullet skill themselves, or is this a pre-built skill they integrate?** Because that changes the scope significantly:
- If they *build* it: this lesson becomes partially about skill-writing again (which feels like scope creep given 02.04 exists)
- If it's *pre-built*: they're just learning to use it strategically, which feels tighter

What's your instinct?

A: Yes exactly right. The Tracer Bullet skill will be a pre-built skill that they integrate.

Q: Perfect. That's a **much tighter scope** than if they had to build it.

So here's what I'm seeing:

**The core takeaway**: After this lesson, they can generate a dramatically better multi-phase plan by integrating a pre-built tracer bullet skill into their prompting workflow — and they can articulate the specific differences between the naive plan and the tracer-bullet-informed plan.

**One more boundary question** — and this is important for keeping scope tight:

When they compare the two plans, **how deep should they go?** 

- Option A (shallow): "Notice that the tracer bullet plan breaks things down into smaller, more concrete steps"
- Option B (medium): "Articulate 3-4 specific ways the tracer bullet plan differs: granularity, testability, clarity, risk mitigation"
- Option C (deep): "For each phase, identify which tracer bullets enabled which improvements, and understand *why* those improvements matter"

Option A feels too hand-wavy. Option C feels like it belongs in 03.06 when they're actually *executing* the plan and seeing the benefits in real time.

**I'm voting for Option B** — they should notice and name the differences, but the *proof* of why tracer bullets matter comes when they actually use the plan to guide the work in the next lesson.

Does that feel right to you? Or do you want them doing more analytical work on the comparison itself?

A: Yeah I think that's right. I think not necessarily articulate but notice three to four specific ways the plan differs. I don't know to be honest; just notice that there should be pretty big differences. We shouldn't have to really train people to see it.

I think noticing that Tracer bullets give you feedback earlier and that they tell you in what ways that you can QA the application to check that all the integration layers work. They give you a chance to or give you opportunities to provide feedback during that step, which is really important.

Q: Ah, **now** I'm seeing the real value proposition. This isn't about abstract plan quality — it's about **feedback loops embedded into the plan itself**.

Let me reframe:

**The core takeaway**: Tracer bullets force you to build plans where you can get feedback and validate integration points *during* execution, not just at the end.

That's **concrete and observable** — and it's why the naive plan will look so different. The tracer bullet plan will have explicit "validate this works end-to-end" checkpoints baked in.

So the lesson structure becomes clearer:

1. Show the naive multi-phase plan (from 03.03)
2. Integrate the tracer bullet skill and re-prompt with the same PRD
3. Compare side-by-side: notice where the tracer bullet plan creates earlier feedback loops and QA checkpoints
4. Don't execute yet — just absorb that this plan is *shaped differently for validation*

**One final scope question**: 

Should they actually run the skill integration themselves (pulling it into the repo, contextualizing it with the PRD), or do you want to give them a pre-generated tracer bullet plan to compare against?

The former feels more engaging and teaches them the workflow. The latter gets to the comparison faster. What's your lean?

A: No yeah, they will definitely run it themselves. This is a skills-based exercise, hands-on.

Q: Perfect. Then I have the full picture. Let me lock this down:

---

**Scope Summary**

**Lesson title**: Use Tracer Bullets to Create a Better Multi-Phase Plan

**Core takeaway**: Tracer bullets reshape your multi-phase plan to include feedback loops and integration validation checkpoints that let you catch problems *during* execution instead of at the end.

**Prerequisites**: 
- Understanding of what tracer bullets are (from 03.04)
- A naive multi-phase plan from 03.03
- A PRD from 02.02
- Familiarity with integrating skills into Claude Code (from 02.03)

**In scope**:
- Integrating the pre-built tracer bullet skill into their repo
- Re-prompting for a multi-phase plan with the tracer bullet skill contextualizing the work
- Side-by-side comparison of the naive plan vs. the tracer-bullet plan
- Noticing that the new plan has earlier feedback loops and explicit QA checkpoints at integration points
- Observing that this plan shape enables validation *during* phases, not after

**Out of scope**:
- Executing the plan (that's 03.06)
- Building or modifying the tracer bullet skill (that's 02.04)
- Deep analysis of *why* these differences matter — the proof comes in execution
- Creating new PRDs or re-scoping features

**Rough flow**:
1. Show the naive multi-phase plan from the previous exercise
2. Walk through integrating the pre-built tracer bullet skill into the repo
3. Use the skill to re-prompt for a multi-phase plan (same PRD, same context)
4. Compare the two plans side-by-side
5. Notice and name the differences: earlier feedback loops, QA checkpoints, integration validation steps
6. Reflect briefly on why this shape matters (teeing up 03.06)

---

Sound right?
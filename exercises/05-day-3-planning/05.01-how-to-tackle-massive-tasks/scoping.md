A: Go

Q: Looking at the course structure and that explainer, I've got a clear read on where this sits:

**Context**: This is **03.01**, the opening lesson of Day 3. By this point, learners have already done:
- Day 1: LLM constraints, codebase exploration, hands-on feature building, and the plan-execute-clear loop
- Day 2: How to steer agents via `agents.md` and skills

So they've *practiced* plan mode in a real codebase. They know how it works at a basic level.

What comes next matters too:
- **03.02** is about writing PRDs (a structured way to define problems)
- **03.03** is about multi-phase plans (breaking work across context windows)
- **03.04** is tracer bullets (a specific technique)

**My initial read**: The explainer says "Plan mode breaks down with very large tasks" — but I think this lesson is actually trying to set up why PRDs and multi-phase plans exist. The danger here is **scope creep**. This could easily become a dumping ground: "Here's what plan mode can't do, here's why context windows matter, here's LLM behavior at scale..." and suddenly you've lost focus.

**My opening question**: 

What's the ONE behavior change you want after this lesson? Is it:
- "I can recognize when a task is too big for plan mode to handle"?
- "I understand *why* LLMs fail on massive tasks and what that means for my workflow"?
- "I can apply some principle (chunking? prioritization?) to break down massive work"?

Because those are three different lessons, and I want to know which one this actually *is*.

A: I think essentially what we're trying to do is take all of the knowledge we've learned so far about Smart Zone and Dumb Zone in the other limbs. We understand what plan mode does but we're trying to follow the natural thing that people discover when they start using plan mode: it can only tackle features that are only so large. How do you actually tackle a huge project or a huge build from the ground up when the LLM only has a certain amount of Smart Zone that it can use in its context before it starts being done? It's essentially setting up the problem that the rest of the section goes on to answer.

Q: **Okay, that's a much clearer picture.** You're not teaching a *solution* here — you're **making the learner feel the problem** they'll solve over the next three lessons.

This changes everything about scope. You're building intuition, not delivering technique.

Let me push back on one thing though: You say "take all of the knowledge we've learned so far about Smart Zone and Dumb Zone" — but I need to check: **Have we actually taught Smart Zone and Dumb Zone explicitly?** 

Looking at Day 1, I see:
- 01.01: "the-constraints-of-llms"
- 01.06: "the-plan-execute-clear-loop"

But I don't see a lesson that *names and defines* "Smart Zone" and "Dumb Zone" as concepts. The explainer references them, but I'm not sure learners have built mental models around those terms yet.

**So before I lock scope, two quick questions:**

1. **Do we need to briefly define/remind learners what Smart Zone and Dumb Zone are?** Or are we assuming they absorbed this from Day 1 naturally and we can just use the terms?

2. **The real question**: After this lesson, should the learner be able to articulate *specifically* what breaks down? Like: "Plan mode fails when [specific observable symptom]" — so they can recognize it when it happens to them? Or is it more abstract: "I understand there's a limit and the next lessons show how to handle it"?

Because that distinction will determine whether this is a 10-minute observation or a 20-minute guided discovery.

A: Yeah it's within the constraints of LLMs. We'll have been referencing it throughout the course so I don't think we need to re-define it here. It's more setting up the idea that there are tasks that are just too big for you to handle in one chunk.

Q: **Perfect.** So you're not re-teaching constraints — you're showing what happens when you *ignore* them by trying to tackle something massive in one go.

Now I need to understand the **experiential arc** here. Because "setting up the problem" can be done two very different ways:

**Option A: Show them the failure**
Have them attempt a genuinely large task in plan mode, watch it deteriorate, feel the pain. Then the next lessons become "here's how to avoid that."

**Option B: Explain the ceiling**
Walk through the math/logic: "Here's your context window, here's how much a typical feature takes, here's what happens when you try to cram 5 features into 1 plan..." More theoretical.

Option A is *way* stickier — learners remember failures they experience. Option B is efficient but abstract.

**Which direction feels right for this course's pedagogy?** 

And related: **Do you have a concrete example task in mind?** Something like "build a complete ecommerce checkout flow" or "add real-time notifications to a social app"? Or is this more conceptual?

Because if you're showing Option A, the example needs to be real enough to actually break, but scoped tightly enough that the lesson doesn't become "here's a 2-hour struggle session."

A: This is a knowledge-based lesson so we're just going to be focused on teaching the raw concept. They will probably come into this day three thinking, "I'm feeling ambitious. How do I use this to tackle massive tasks?" This is setting up that question for them and then elaborating it for them before actually showing them the solutions in the next few exercises.

Q: **Got it. Knowledge-based, not hands-on.** You're managing expectations and building the mental model before they hit the solutions.

So the arc is: "You're feeling ambitious → here's why that ambition hits a wall → now we'll show you how to work around it."

**Let me nail down the core takeaway then:**

After this lesson, the learner should be able to articulate:
- **What breaks down**: Plan mode works for feature-sized tasks, but genuinely massive projects don't fit in one context window before the LLM enters the dumb zone
- **Why it matters**: Trying to ignore this leads to degraded output, not just inefficiency
- **What's coming**: There are structured approaches to handle this (which the next lessons teach)

Is that right? And more specifically — **can they pass a simple test like**: "I try to plan a 3-month project in one shot. What will happen and why?"

Also: **How much time/depth?** This feels like a 10-15 minute lesson (read + maybe one small example scenario). Are we in that ballpark, or does this need to be meatier?

One more thing I'm thinking about: **The title** "How To Tackle Massive Tasks" is backwards for what this lesson actually does. It promises solutions but delivers problem-setup. Would something like **"Why Plan Mode Has Limits"** or **"Recognizing When Tasks Are Too Big"** be more honest? Because setting expectations right matters for the learner's mindset going in.

A: Yeah I guess why massive tasks are a problem for. I don't know; I feel comfortable with the title but I see where you're coming from.

Q: **Fair.** The title works if we're reading it as "Here's the approach to tackling massive tasks: first, understand why they're hard" — that's defensible. Keep it.

Alright, I think we're close. Let me lock this down:

**One last boundary question**: How much should we actually *talk about* the solutions that are coming? Like:

- Do we mention "hey, PRDs exist and they help" and then move on?
- Do we name multi-phase plans and tracer bullets as concepts without explaining them?
- Or do we stay totally in the problem space — no spoilers, just "here's why it's hard"?

I ask because there's a risk of this lesson becoming "here's the problem AND also here's the menu of solutions coming up," which dilutes focus. **I'd lean toward**: Stay in the problem. Make it vivid enough that learners *want* the solutions. Let 03.02, 03.03, 03.04 each land as a surprise.

Does that feel right, or do you think we need to hint at the solutions here?

Once you answer that, I'll give you the **Scope Summary** and we can lock this in.

A: Yeah I think the next lesson is setting up and writing a PRD. We should explain what the overall stack is for tackling these kinds of problems I suppose. Maybe we use the PRD as a software practice, building up huge great big specs before you go in.

Q: **Okay, so you want to hint at the overall *strategy* without teaching the tactics yet.** That makes sense — give them the map before you hand them the compass.

So the stack would be something like: "To handle massive tasks, you need to break them into smaller chunks. One way to define those chunks clearly is with a PRD. Another way is to split across multiple context windows. Another is to use tracer bullets." Then **03.02 dives deep on PRDs as *one approach* in that toolkit.**

**But here's where I want to push back slightly**: If we explain all three approaches (PRD, multi-phase, tracer bullets) at a high level in this lesson, we risk:
1. Making this lesson feel like a table of contents instead of a focused concept
2. Stepping on the toes of 03.02, 03.03, 03.04 — they each become "here's the deep dive on [thing we already explained]"

**My suggestion**: Name the problem clearly. Maybe hint that "there are structured approaches" without listing them. Let each *next* lesson introduce its own approach as the answer to "okay, so how do we actually do this?"

Think of it like: This lesson is "Why do we need structure?" The next three are each "Here's one kind of structure that works."

**Does that feel right?** Or do you think learners need to see the full menu upfront to orient themselves?

A: Yeah we definitely shouldn't. We should just focus on what a PRD is and they might even have seen them in their work, right? They definitely don't need to learn the full menu up front. Tracer bullets, especially, will be a kind of a really cool revelation when we get there and we don't really need to tease it earlier. Multiphase, we don't even really need to tease. We can just sort of say, okay this is the problem and then when we get to multiphase, we'll figure out the solution.

Q: **Perfect.** That's exactly right. Stay in the problem space. No menu. No setup for future lessons.

So we're back to the clean scope: **This lesson is purely about recognizing and understanding why massive tasks break plan mode.** The solutions come when they come.

One final clarification though — you mentioned "focus on what a PRD is" — **do you mean:**

A) We explain what a PRD is as context for "here's one tool that helps" (but don't teach *how to write* one — that's 03.02)?

B) We just acknowledge PRDs exist without explaining them?

Because if it's (A), that's still teaching a bit of the solution in a "setup" way, which contradicts what we just said about staying pure in the problem space.

I think the cleanest version is: **Just the problem.** No PRD mention. No "here's a thing that helps." Just: "Here's why plan mode maxes out, here's what that means for ambitious projects, here's what you'll experience when you hit that wall."

Then 03.02 opens with "One way to solve this is with a PRD" as a fresh idea.

**Does that feel cleaner, or am I being too precious?**
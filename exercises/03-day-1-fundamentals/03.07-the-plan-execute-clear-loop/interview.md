A: So at this point in the course, the users understand what plan mode is. This is a Claude Code course. They understand that they can see the used context in their status line in Claude Code so they will be able to make good decisions about the amount of context that they're using. The idea of this exercise is to try out plan mode, having learned about it in the previous exercise, to build a feature. The focus is on plan mode, on how to use it, how to get the most out of it, and to actually have a go at doing it.

Q: Oh nice! So this is a **hands-on exercise where they actually *use* plan mode** to build something real. That's a great way to cement the learning. Love it.

So if I'm understanding the vibe here:

1. **The core focus** = Teaching plan mode through doing — they'll use the planning/executing/clearing loop to build this comment system feature
2. **The "aha" moment** = Understanding how to structure their thoughts, break down the work, and execute without getting lost in context
3. **The practical angle** = They'll see the context meter actually help them make decisions about scope and execution

A few angles I'm thinking could make this a solid interview:

- **How plan mode helps with feature complexity** — Comments systems have a few moving parts (visibility rules, admin features, etc). How does planning help untangle that?
- **The decision-making process** — When do they decide to execute vs. keep planning? How do they know when a plan is "good enough"?
- **Real debugging/recovery** — What happens when the plan hits reality? How does plan mode help them course-correct?

Which of those resonates most with you? Or is there a specific aspect of plan mode you want to spotlight — like the context awareness piece, or the psychological benefit of having a written plan before you start coding?

A: I think we mostly just want to focus on the steps to complete for this exercise.

Q: Got it! So you want to keep this straightforward — just walk through **what they need to do to complete the exercise**, step by step.

So that would be something like:

1. Set up the comment system (database/data structure)
2. Build the student-facing comments feature
3. Add the admin/instructor hidden comment functionality
4. Create the separate admin view page
5. Test it all works

And the interview will focus on **how to use plan mode to tackle each of these steps** — planning the approach, executing, clearing context, repeat.

Does that capture it? Should we also mention checking the context meter as they go to make sure they're staying within reasonable bounds?

A: Let's go live! Start the interview based on what we discussed.

Q: Perfect! Let me kick this off.

---

Hi! I'm here to chat with you about this exercise on the Plan/Execute/Clear loop. I've reviewed the brief — it's a lesson comment system where students can leave comments, and instructors/admins can hide comments and view them in a separate space.

So here's my first question:

**When you start this exercise, what's your instinct for the very first step you'd tackle?** Would you jump straight into building the database structure, or would you approach it differently?

A: So first thing you should do is kick off plan mode by hitting Shift Tab twice. This will put you in plan mode in Claude Code. From there you can start talking to the agent about what you want to build. In this case we're building a comments system. You can really take this as far as you want. In the exercise you can build just a very simple comment system or you can build instructor and admin hiding comments and that kind of thing. View all comments for instructors and admins or that sort of thing. Even comment stats if you fancy.

What I would say is to talk to Claude Code about what the scope of it should be and what you want to build. Then with Claude Code you can start walking down the design tree of all the design decisions that you can anticipate before getting into code.

Q: Ah, that's really helpful! So the **very first move** is hitting Shift+Tab twice to enter plan mode, then having a conversation with Claude Code about scope and design *before* any coding happens.

I'm picking up on something interesting here — you're saying they should **talk through the scope with Claude Code first**. 

So when they're in that initial conversation about what to build, **what kinds of design decisions should they be anticipating and discussing?** Like, are we talking database schema, component structure, API endpoints, or something else entirely?

A: Exactly. Database schema, roots, API endpoints, component structure, all that stuff.

Q: Got it. So they're mapping out the whole architecture in plan mode before touching any code.

Here's what I'm curious about: **Once they've walked through all those design decisions with Claude Code and have a solid plan written out, how do they know when it's time to switch from planning into executing?** Is there a moment where they say "okay, plan is good enough, let's start coding"?

A: When you have a shared feeling of "OK the AI understands what I need," you can review the design document or not. You can either choose to review the plan or not review the plan and then from there you can jump in.

Q: Nice. So it's less about a checklist and more about a **gut feeling that you're on the same page** with Claude Code.

Once they jump into execution mode — they hit Shift+Tab once to execute — **what should they be watching for?** Like, are they checking the context meter to make sure they're not blowing through tokens, or is there something else they should be monitoring as Claude Code starts building?

A: Exactly. At the moment that they switch from Execution Mode, Claude Code will offer them a choice. It will offer them the choice to either clear the context and just use the plan or just use the plan or just to go from there.

Now that depends on how much context you've already used. If you used a lot of context talking with Claude Code then you should be wary about jumping into execution with all of that context still in. If you're still at, let's say, 20% context, you might feel, "OK I can do this myself or I don't need to clear my context at this point." They should be watching their usage in the status line like a hawk to make sure that they're not slipping into the dumb zone.

Q: That's a great distinction — so they're really **managing their context budget as they go**, using that status line to make decisions about whether to clear or keep the context.

So here's what I want to clarify: **When they do decide to clear context and just work from the plan, what does that actually mean for how Claude Code behaves?** Does it forget everything from the planning phase and only see the written plan, or does it still have access to the code that's been written so far?

A: Yeah it's exactly right but we've covered this in the previous exercise.

Q: Right, of course — they've already learned this in the previous exercise on plan mode.

So once they're executing and building out the comment system, **how many times do you expect them to cycle through this loop?** Like, is it one big plan-execute-clear cycle, or should they be planning, executing, clearing, then planning again for different features (like maybe one cycle for the comment posting, another for the admin hiding feature)?

A: As they're going they might find that they need to. If they end up in a situation where they're scared about the amount of context they're using, they should follow these steps.

They should first tell Claude to output the plan to a local file, as well as a progress report and everything that's been done so far. When they do that they should be able to clear the context using /clear and then restart it by pointing it at this plan and the progress report. With the plan, the progress report, and the changed files in git, Claude should be able to restart pretty effectively. They should not necessarily, or it depends on what size of scope they've chosen for the feature, but they probably won't hit that. We'll talk about multi-phase plans later in the course.

Q: Got it — so they have an **escape hatch if context gets scary**: dump the plan and progress to a file, clear, and restart from those artifacts plus the git diff.

That's a solid safety net. So let me ask this: **When they're actually executing and building features, what should they be asking Claude Code to do first?** Like, should they say "build the database schema," or should they be more conversational about it — asking Claude to help them think through implementation details before it starts coding?

A: I think they should ask Claude for its implementation plan and sort of iterate on it until it sounds sensible.

Q: Ah, so **even within the execution phase**, they're still doing a mini planning cycle — asking Claude for *its* implementation plan for the specific feature, iterating on it until it feels right, *then* telling it to build.

**How many rounds of iteration on that implementation plan do you typically see before it's ready to go?** Is it usually one or two back-and-forths, or does it vary wildly depending on the complexity of what they're building?

A: I've got you; I misunderstood. No this is during the planning phase. They should be asking for its implementation plan.

During the implementation you can sort of step back and just sort of watch Claude go. If it's doing anything stupid or if it's doing something you don't like, you can stop it. You can press Escape and you can then say, "No, you should probably do this instead." So add a bit of steering into it.

Q: Ah, that makes sense! So **during execution, they're mostly watching and letting Claude Code run** — it's hands-off unless something looks wrong, then they can jump in and steer.

So here's the practical question: **What does "stupid" or "wrong" actually look like in practice?** Like, are we talking about obvious bugs, or is it more subtle — like Claude taking an approach that doesn't match the design decisions you made in the planning phase?

A: It might just be:
- using AI Hero
- you're always on the lookout for hallucinations or choosing stupid libraries
- it might be just obvious bugs
- or it might be something that doesn't match the rest of the project, like using the wrong casing in a file name or something
You'll know it when you see it.

Q: Fair enough — "you'll know it when you see it" is pretty honest!

So once they've built out the comment system and everything is working, **what should they do at the end of the exercise?** Like, is there a final step — testing it, reviewing the code, writing documentation — or do they just call it done once the features are built and working?

A: Yep as a final step you should be testing it, reviewing the code, and checking that it works and that everything that you described in your scope is up to date. If it's not up to date and you notice some clear bugs then you can go with Claude again either by clearing and starting a new plan or if you've still got context budget left in the Smart Zone, you can do it within that context window too.

Q: Perfect. So it's a full loop — **plan, execute, test/review, and then decide if you need another cycle** based on what you find.

One last thing: **For someone doing this exercise for the first time, what's the biggest mistake you see people make?** Like, do they skip the planning phase and jump straight to coding, or is it something else?
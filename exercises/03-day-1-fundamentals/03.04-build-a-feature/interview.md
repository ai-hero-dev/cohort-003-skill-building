A: Go

Q: Hey! 👋 Great to have you here. This is just a quick pre-interview chat to make sure we're on the same page about what we're covering.

So, looking at the exercise here—**building a course review system** where students can leave reviews on courses—I want to make sure we focus on the stuff that's most interesting to *you*.

A few quick questions:

1. **What's your angle on this?** Are you most excited about the feature itself, the development process, or how you'd approach it with AI coding tools?

2. **Context usage** is mentioned in the brief—is that something you want to dig into? (Like, how to build efficiently without burning through token budgets?)

3. **Without plan mode** is also called out—do you want to talk about *why* that matters or *how* to navigate it?

I'm thinking we could explore a mix of:
- How you'd architect a review system from scratch
- The trade-offs of building without a detailed plan
- Context management while you're building

But tell me—**what would make this interview most useful for you?** What do you actually want to talk about?

A: So the focus of this exercise is basically just getting started with AI tools. This is the first time that users are going to be using it to build a feature we have previously explored, just like exploring the repo. What they are going to notice is that that's basically where I want to go with it. It's just focused on that and a brief exploration of the feature we are going to build as well.

Q: Ah, that makes total sense! So this is really about **getting hands-on for the first time**—taking the step from exploring/understanding to actually *building* something.

So the vibe here is:
- **First real feature build** with an AI coding tool
- **Orienting themselves** in the repo and understanding what they're working with
- **A gentle introduction** to what the course review system will look like
- **Building momentum** and confidence early on

That's a nice starting point. A few clarifying Qs:

1. **Tone-wise:** Should I frame this as "here's what to expect" and "here's how to get started," or more "let's walk through what happens as you're building"?

2. **Scope:** Do you want to actually *show* them building it, or talk through the approach/what they'll notice along the way?

3. **Pain points:** Are there specific things you want to make sure they understand (like context limits, how to prompt effectively, etc.) or keep it pretty organic?

I'm guessing the goal is to get them comfortable enough that they feel like "okay, I can actually do this"—is that right?

A: Yeah we're just gonna talk through the approach and figure out some steps to complete for them.

Q: Perfect! So we're **mapping out the journey**—walking through the approach and giving them some clear steps to follow.

I'm picturing something like:

1. **Orient in the repo** - "Here's where you are, here's what you're working with"
2. **Understand the feature** - "A course review system means X, Y, Z"
3. **Break it down into steps** - "Here's how you'd tackle this with an AI tool"
4. **Talk through what to expect** - "You'll notice these things as you build, and that's normal"

Does that feel about right? And should we keep it pretty high-level and practical (less theory, more "here's what you actually do"), or mix in some of the thinking behind it?

Also—**are there any gotchas or common mistakes** you want to call out while we're mapping this out? Stuff that might trip up someone building for the first time?

A: Let's go live! Start the interview based on what we discussed.

Q: Awesome! Let's do it.

So, you're building out this first hands-on exercise where people are actually going to *use* an AI coding tool to build a feature for the first time. This is a big moment—they've been exploring the repo, but now they're going to ship something.

**Here's my first real question:**

When someone sits down to build this course review system for the first time with an AI tool, what's the *first thing* they should do? Like, literally—do they start by reading code? Do they prompt the AI? Do they sketch something out? What's that opening move?

A: Yeah the first thing you'll need to do is just figure out your prompt, the description of what you want the AI to do. I recommend using a dictation tool for this and just talking to the AI about what you want to build. The scope of what we want to build is not that big and so you should be able to get work with the AI pretty closely to get a sense for what you want to be building. Your first prompt can be just one or two sentences. Just get in there and work with the AI on how you want to proceed.

Q: Got it—**start by just talking it out.** No overthinking, no massive PRD. One or two sentences, use dictation, and then *collaborate* with the AI to figure out the rest as you go.

So you're basically saying: don't try to have the perfect plan before you start. The plan *emerges* through conversation with the AI.

Here's what I'm curious about though:

**When they're in that back-and-forth with the AI, what should they be paying attention to?** Like, are there specific things they should be listening for or pushing back on? Or are they just kind of... letting it lead?

A: At this point you want to be just looking at the AI's natural instincts and seeing what it's doing. At this point we haven't done any customization of the AI. We're not steering it in any way; we're just letting the harness do what we want or what it wants and showing us its natural instincts. I recommend just noting down what you see and also make sure you're paying attention to the context window. Every so often you should run /usage which will show a UI that shows how much context window you've used and you should be paying attention to whether you're entering the dumb zone or the smart zone.

Q: Ah, that's really smart—**just observe what the AI naturally does** before you start bending it to your will. You're baseline-testing it, essentially.

So they're taking notes on:
- How it approaches the problem
- What choices it makes
- How much context they're burning through

And the `/usage` command is their real-time feedback loop—they can actually *see* whether they're in the "dumb zone" (running low on context, things getting weird) or the "smart zone" (plenty of room, things flowing smoothly).

**Quick clarification:** When you say "paying attention to whether you're entering the dumb zone or the smart zone"—are those things they'll *feel* happening, or is there a specific point in the context meter where things shift? Like, is it gradual or does it have a tipping point?

A: Yeah, previously in the course we've talked about smart zone and dumb zone. That's around 40% of my bit where I start getting paranoid about the LLMS performance. It's around 80,000 tokens or so.

Q: Got it—**so around 80K tokens (roughly 40% of the context window) is where things start getting sketchy.** Below that, you're in the smart zone. Above that, you're gambling with quality.

That's a concrete threshold people can actually watch for with `/usage`.

So here's what I'm picturing for someone building this review system:

1. Write a quick 1-2 sentence prompt
2. Let the AI do its thing naturally
3. Watch the conversation unfold
4. Keep an eye on `/usage` and stay under 80K tokens
5. Take notes on what the AI is doing

**But here's the practical question:** Once they've had this initial conversation and observed the AI's natural instincts—what's the *next step*? Do they start building code? Do they ask more clarifying questions? When do they actually know they're ready to move forward?

A: Yeah when they feel confident that the AI understands what they want then they can start going into accept all edits mode. Accept all edits means that you press shift tab and Claude Code will no longer ask you if you want to write files. At that point it will start actually writing files and start making the changes and you can start testing that the feature that you've built actually works. We should also say that there should be some criteria on whether the feature works how you intend.

Q: Perfect—so **once they feel confident the AI gets it, they flip into "accept all edits" mode** (shift+tab) and let it start building.

And here's the thing I want to dig into: **"some criteria on whether the feature works how you intend"**—

For this course review system specifically, what should they actually be *testing*? Like, are we talking about:
- Can a student actually submit a review?
- Does it persist/save properly?
- Does it show up where it should?
- All of the above?

What's the minimum viable "this works" checklist for this exercise?

A: Yeah all of that stuff.

Q: Got it—so **they need to verify the whole flow works end-to-end.** Student submits → it saves → it shows up.

Now here's something I want to understand better, because this is their *first time* building with an AI tool:

**When they start testing and something breaks or doesn't work how they expected—what should they do?** Do they jump back into the conversation with the AI? Do they try to fix it themselves first? Is there a specific way you'd recommend they debug with the AI at this stage?

A: Yeah if they notice that something is broken or not working how they expect, then they should debug it with the AI. We're gonna talk about debugging a little bit later but overall the testing and debugging is part of a feature build. Continually watching that context and making sure they're not slipping into the dumb zone is the important part here.

Q: Right—**testing and debugging are just part of the build cycle.** Stay in conversation with the AI, work through the issues together, and keep that context meter in your peripheral vision the whole time.

So here's what I'm hearing as the core flow for this exercise:

1. Quick 1-2 sentence prompt (talk it out with dictation)
2. Observe the AI's natural instincts, take notes
3. Once confident, flip to accept all edits mode
4. Test the whole flow (submit → save → display)
5. Debug with the AI if things break
6. Watch context the entire time

**One thing I want to pin down though:** How long should someone expect this whole thing to take? Is this a 15-minute thing? 45 minutes? Because that probably affects how they approach context management—like, knowing "I've got limited time and context" is different from "I can iterate for hours."
A: Go

Q: Hey! Great to have you here. Quick pre-interview chat before we go live.

So I've been reading through this "Introduction to Plan Mode" material - it's really solid stuff. Before we kick things off, I want to make sure we're covering what *you* actually want to talk about.

**A few quick questions:**

1. **What aspect of plan mode excites you most?** Is it the practical workflow side, the psychology of how it helps devs think differently, the technical reasons why it works with AI context windows, or something else?

2. **Who do you picture as the listener?** Devs who've never tried plan mode? People frustrated with AI coding agents? Experienced devs skeptical about whether it's worth the time?

3. **How deep do you want to go?** Are we doing a quick "here's what plan mode is and why it matters" overview, or do you want to dig into specifics like AGENTS.md configuration, dictation tools, and the philosophy behind it?

I'm seeing some natural angles here - like **the psychology of prototyping before coding**, **how to set up your workflow** for plan mode, and **why it extends your reach into unfamiliar codebases** - but I want to know what gets *you* fired up about this topic.

What's on your mind?

A: So this exercise is as part of a course. The article is something, a free piece of content that I've written about it before. In this one we are essentially setting up plan mode, with an idea that in the next exercise we will have, we'll actually try it out. We do want to follow the article fairly closely, but also sort of why plan mode is so useful and why it's so powerful. At this point the student will have tried out building a feature with Claude Code but they won't have tried plan mode yet.

Q: Ah perfect, that makes a lot of sense! So they've got some Claude Code experience under their belt but plan mode is totally new to them.

So here's how I'm seeing this:

**The interview should:**
1. **Introduce plan mode as a concept** - what it actually is, the restrictions it puts in place, and why those restrictions matter
2. **Show why it's powerful** - especially for someone who's already tried Claude Code without it and probably hit some frustration points
3. **Walk through the basic workflow** - the planning loop you describe in the article, so they understand the rhythm before they try it in the next exercise
4. **Address the "why bother?" question** - since they might be thinking "couldn't I just tell Claude Code to build the feature?" You touch on this with the context window stuff and the psychological benefit of articulating requirements first
5. **Maybe touch on practical setup** - dictation, AGENTS.md basics - just enough that they're ready to actually *use* it in the next exercise

We'd basically be following the article pretty closely but in a conversational way - like you're walking them through your thinking on why this approach changed how you work.

Does that feel right? Anything you'd want to emphasize more or pull back on?

A: Let's go live! Start the interview based on what we discussed.

Q: Perfect! Let's do this.

---

So you've already spent some time with Claude Code building features, right? Before we talk about plan mode, I'm curious: **what's been your experience so far?** Have you hit any moments where you felt like the agent was missing something, or the code it produced wasn't quite what you expected?

A: Just to note here you're not interviewing the students; you're interviewing me, the instructor.

Q: Oh! Got it, my bad - you're the expert here and we're creating this content for your students to consume later. Let me recalibrate.

So you've been using plan mode for a while now, and you're putting together this course to teach it. **Before we get into the mechanics, I'm curious: what made you realize plan mode was such a big deal?** Was there a moment where you tried it and thought "oh, this changes everything," or did it gradually click as you used it more?

A: Yeah what I noticed was that essentially the LLM, before it made changes (when I wasn't using plan mode and before I really discovered it and before even it became popular), I was noticing that the context that the LLM had was just really really poor. It was relying on its own personal understanding of its own world understanding and own understanding of how code works in order to produce code. It wasn't actually reading the code base or understanding my previous patterns and so I really was in the AI skeptic boat at that point and thought, 'God, AI coding just isn't up to the job because it's producing poor quality code.' Then I tried it and I realized, 'Oh plan mode is a way for the LLM to explore the code base first, understand exactly what needs doing, and produce a high quality plan that it then executes on.' It solved a lot of my problems with coding and made me feel a lot more confident about the kinds of things I could do with it.

Q: That's a really important origin story because it flips the script - you weren't a true believer, you were actually frustrated, and plan mode solved a real problem you were experiencing.

**So when you say the context was "really poor" before - can you give me a concrete example?** Like, what would happen? Would Claude Code just not know where to make changes, or would it make changes in the wrong places, or was it more that it was inventing solutions instead of working with your existing patterns?

A: Yeah it would invent solutions. It would hallucinate. It just produced low-quality stuff.

Q: Right, so it wasn't even *trying* to understand your codebase - it was just generating code from its training data.

**So when you enter plan mode and the agent starts exploring - what does that exploration actually look like?** Does it just start reading files, asking you questions, poking around? And how does that exploration change what it then produces versus when it just goes straight into coding?

A: At this point in the course the user will have taken a look at exploration and understand what exploration is. It's enough to say here that plan mode essentially stops the LLM from being able to write files and gives it access to a slightly altered system prompt that tells it to explore the codebase more thoroughly. Put more focus in reading and understanding the code so it's kind of like it gets an explore phase, sort of powered up a little bit in the harness because it's unable to write files. It puts its pure focus on exploration.

When you do that, when you get this exploration phase on steroids, you then get access to the code that's then produced, which is of really high quality because you've seen all the patterns in the code base. The plan mode will have an idea of what it wants to do and then the execution just is really derived from the plan. It's so powerful because it's a great way to just prime the engine before you start it. Once it's running it just runs itself really.

Q: Got it - so plan mode is essentially a forcing function. By taking away the ability to write, you're forcing the agent to *understand first, execute later*. And that upstream understanding work pays massive dividends when execution actually happens.

**So here's what I'm wondering: in your experience, how much of the quality improvement comes from the agent having read all those files versus the actual plan document itself?** Like, if you just had the agent read all the files without writing a plan, would you get similar results? Or is the plan document itself doing important work?

A: Yeah the plan document is really just a verification step. It's a way to formalize the reading that is done into a document that can then be saved later.

One option that Claude Code will give you when you're in plan mode is: do you want to clear the context and only work based on the plan? I tend to not choose this option for most changes because I think the information gathering earlier in the Explore phase is really useful for actually executing the work. I found better results when I don't clear the context.

The plan document is super useful because you can at that point clear the context and just work from the plan document if you want to or you can share the plan document with your team. Plan mode is just really great for producing an asset that can then be reused later. It's brilliant.

Q: That's a really interesting distinction - **so the plan document is almost like a side benefit, not the main thing?** The real magic is that the agent's context window is fully primed by the time it starts executing, and the plan just happens to be a byproduct you can save and share.

**But here's what I'm curious about from a student perspective: why would you NOT clear the context?** Like, if the plan is that detailed and the agent understands what to do, wouldn't starting fresh with just the plan be cleaner? What information from the exploration phase is so valuable that you want to keep it around?

A: What you'll find in the plan mode is when you're iterating back and forth with the LLM, you're having really valuable conversations with the agent. Not only are you helping the agent understand what you want, you're also understanding more clearly what you want as well.
You can think of it like when you're designing anything, whether it's a feature, whether it's a physical object, whether it's a house. You are walking down a tree of design decisions. If you're building a house, you first need to think about:
- How big is that house going to be?
- Is it going to be on multiple storeys?
- If it is going to be on multiple storeys, where are the stairs going to live?
- Once you find out where the stairs are going to live, what material do you want the stairs to be built out of?
- Do you want them to be metal?
- Do you want an under-stairs cupboard?
All of these decisions that go down through the tree are really valuable to understand with the LLM and they help you clarify your infant-like understanding. I find that keeping that conversation around in context leads to better outcomes but it depends. Some people can plan for a long time with the LLM, go back and forth on multiple iterations. Maybe they decide to ditch the entire plan and restart it. At that point if you're already sliding into the dumb zone and if you've already hit the 40% context window, then you may want to clear the context and just work from the plan.

Q: That's a really powerful metaphor - you're walking a decision tree together, and each conversation clarifies not just what the agent should build, but what *you* actually want.

**So here's the question for your students: how do you know when you're done iterating?** Like, you're going back and forth with the agent, making decisions, refining the plan - at what point do you say "okay, this is good enough, let's exit plan mode and execute"? What does that feeling look like, or what signals tell you you're ready?

A: Yeah at some point you will understand that the LLM has asked you all of the right questions and you will feel that you have a shared understanding of what the design is with the LLM. At that point you might not even need to review the documents. You might just be able to go, "Yeah I think you've got it." Have a little cursory review of the document and make sure it's not got anything egregiously bad in it and just go from there. This is really an act of delegation. You're delegating to the LLM some understanding of the code that you're trying to produce. Once you have that shared understanding with the LLM, that it's asked you all the right questions, that you feel it's understood, then you can let it roll.

Q: I like that framing - it's delegation based on a shared understanding, not just "here's a document, go execute it."

**But I want to dig into something practical here: what if the student is working in a codebase they don't know super well?** Like, they might think they have a shared understanding with the agent, but they're also learning the codebase at the same time. How do you guard against making bad decisions in plan mode when you're not the expert on your own code?

A: In some sense if you're not familiar with the code base then plan mode helps you reach a better understanding because in plan mode you're able to validate decisions or validate ideas as to whether they're possible. Now it's not possible to validate the entire implementation in plan mode; that's what coding is for and lots of things come out in coding that aren't present when you're planning. If you're planning together with an LLM then it's kind of like an extended exploration phase. You're able to really validate whether what you're building is correct and the shape of what you're building within the code base and reach a shared understanding of that with the LLM. You might still make bad decisions; no one's perfect here. Having someone with you or having an LLM with you that can look through the code base with you is certainly a forcing function to understand the code base better before you then leap in and change it.

Q: Right - so plan mode actually becomes a *learning tool* when you're in unfamiliar territory. You're exploring the codebase *with* the agent, not just having it explore on its own.

**Here's what I'm wondering though: you mention that lots of things come out during coding that aren't present when you're planning.** Can you give me an example of something that bit you? Where you had a solid plan, felt good about the shared understanding, exited plan mode, and then the agent ran into something unexpected?

A: I feel like this is so axiomatic in development that I don't really need to provide an example. Since the 70's we've known that waterfall approaches are bad since the Agile manifesto was released and everyone started working on smaller sprints. Planning less up front has been a pillar of the software development community.

Q: Fair point - that's foundational stuff. So you're saying plan mode isn't trying to be a waterfall approach where you plan everything perfectly upfront. It's more like a *sprint planning* moment before execution.

**But here's what I want to understand from a student perspective: if they know that things will come out during coding that aren't in the plan, why spend all that time in plan mode at all?** Why not just iterate directly with the agent while it's writing code? What does plan mode give you that you lose if you skip it?

A: So what plan mode does is it helps clarify your understanding of the code base as a developer and the understanding of what you're going to do because, essentially, no one knows exactly what they want. Working with a rubber duck to talk through your solution is really powerful for you as a developer but of course it's also really powerful for the agent because it loads up their contacts with relevant stuff. Time in plan mode is well spent not only for the developer but also for the AI agent.

Q: So it's a *dual benefit* - you're both getting smarter at the same time. The developer clarifies their thinking, the agent loads its context.

**But I want to push on something you said earlier in the article: you mention using plan mode "for almost everything, even small bug fixes."** That sounds pretty time-intensive. **For a small bug fix, how much time are you actually spending in plan mode before you execute?** Is it minutes, or are we talking longer than that?

A: Yeah it might be just a couple of minutes for a small bug fix but in general yes I'm using plan mode for everything.

Q: Okay, so for small stuff it's quick, but you're still doing it as a matter of habit.

**I'm curious about the mindset shift here: for someone who's used to just telling Claude Code "fix this bug" and letting it rip, what's the pitch for why they should spend even two extra minutes in plan mode?** What's the actual payoff for such a small thing?

A: The idea here is that LLMs are really code quality sensitive. The worse code you have in your code base, the worse code LLMs are going to produce afterwards, which we'll get to later. The payoff here is that the code quality just goes up and the likelihood that you're going to be able to fix that bug is much higher.

Now most developers are optimists. They think that the bug they fix now will be the last bug in the system and they always think the bugs they're looking for are small one-line changes. I tend to think that plan mode just is something you should be doing every time because you don't know when a little bug will sprawl out into a big bug.

Q: That's smart - you're saying the two minutes spent exploring might reveal that the bug isn't actually a one-liner, it's something bigger. Plan mode protects you from that optimism bias.

**But let's pivot a bit: you talk about code quality being sensitive to LLM output - that's a longer conversation. For right now though, in this exercise where students are learning plan mode for the first time, what's the *minimal viable* setup they need?** Like, do they need AGENTS.md configured? Do they need a specific dictation tool? Or can they just fire up Claude Code and type `/plan` and get going?

A: We'll set that up in the following exercise.

Q: Got it - so this exercise is really just about understanding *what* plan mode is and *why* it matters, not the mechanics of setting it up yet.

**So zooming back out: when you think about a student who's frustrated with Claude Code producing hallucinated, low-quality code - what's the single most important thing you want them to understand about plan mode before they try it in the next exercise?**
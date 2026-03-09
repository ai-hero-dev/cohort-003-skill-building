A: Go

Q: # Pre-Interview Chat: AGENTS.md

Hey! Welcome! 👋 So glad you're here. Before we roll cameras, let's do a quick chat about what you want to focus on for this interview.

I've got the article here about **AGENTS.md files** — the whole "how to keep them lean and effective" angle. 

**Quick question for you:** What part of this topic gets you most excited? Are you more interested in:

- **The practical "how-to"** — like, walking through the refactoring process step-by-step?
- **The philosophy** — why keeping AGENTS.md small actually matters for agent performance?
- **The architecture stuff** — how monorepos and progressive disclosure work together?
- **All of it?** (We can do that too!)

Also, is there anything you'd want to **add** or **emphasize** that might not be super obvious from the article? Like, a particular gotcha you've seen in the wild, or a story about a AGENTS.md that got out of hand?

Let me know and we'll lock in the scope! 🎬

A: Yeah I think we want to touch on what an agents.md file is and to be honest I want to focus this mainly on claude.md. This is going to be a Claude code workshop and so Claude actually doesn't support agents.md; it supports claude.md but other than that the logic is exactly the same. I've included an article here about what claude.md actually is and what it does and kind of what you can get out of it. I suppose we're looking for a philosophy here.

In the next exercise after this we're going to try it out with Claude code so we don't necessarily need the practical stuff so much. It's more about the philosophy of what you put there, why you put it there, and honestly why you might need to steer an AI coding agent in the first place.

Q: # Perfect—That's A Great Angle

Okay, I **love** this direction. So we're pivoting to **Claude.md** specifically, and keeping it philosophical rather than practical. That makes total sense for a workshop flow—you're building the *why* first, then the *doing* comes next.

So here's what I'm hearing:

1. **What is Claude.md?** — Quick explainer so people understand what it is and where it sits in the context
2. **The philosophy of steering** — Why do you even *need* to steer an AI coding agent in the first place? What goes wrong if you don't?
3. **The instruction budget concept** — That idea that you've got limited tokens and conflicting priorities
4. **Less about the mechanics** — No deep dive into progressive disclosure patterns or file structure (that's the *next* workshop)
5. **More about principles** — What should guide your thinking when you're deciding what goes in Claude.md?

Does that capture it? And just to confirm—should we mostly stick with the Claude.md angle and just briefly note "hey, AGENTS.md is the same idea for other tools"? Or would you want to spend a bit more time comparing the two?

Once you confirm, we're locked in and ready to roll! 🎬

A: Let's go live! Start the interview based on what we discussed.

Q: # Interview: Claude.md and Steering AI Coding Agents

Alright, let's do this! 🎙️

So I've reviewed the article on AGENTS.md, and I know that Claude Code actually uses **Claude.md** instead—but the philosophy is basically identical. Before we get into the weeds, let me start with the most fundamental question:

**Why does Claude.md even exist in the first place? Like, what problem is it actually solving?** 

Is it just "Claude Code is too dumb without it," or is there something deeper going on about how AI agents interact with your codebase?

A: That's a great question. Claude.md exists because you need some mechanism for steering Claude code. Essentially you think of the way that you can provide inputs to the LLM.

You've got your prompt first of all. You've then also got the code base and inside the code base you could put information that the LLM can find if it needs to, such as documentation or code patterns or the code itself. You've also probably got a git history it can explore too.

One thing you don't have out of the box, if we imagine claude.md didn't exist, is a way to provide context that was needed on every single request. That's the problem and that's what claude.md does. Every single time you send a request to Claude, the claude.md file gets sucked up into context and gets provided along with it. This is great for when you want to provide some kind of global instruction that lives in every single request.

Q: # That's A Crucial Distinction

Okay, so Claude.md is **always there**, right at the top of every conversation. It's not something the agent has to discover or navigate to—it's baked into the context from the jump.

So if I'm thinking about this correctly: you *could* theoretically put all your conventions and guidance into a README or a docs folder, and Claude Code would find it. But that's reactive—the agent has to know to look, and it only loads that context when it's relevant.

**But Claude.md is proactive.** It's *always loaded*, *always available*.

Here's what I'm curious about though—**and this is the philosophical bit**—why would you *want* something on every single request?

Like, what's the difference between "I want this guidance present at all times" versus "I want the agent to be able to find this when it needs it"? Why not just let Claude Code navigate your docs?

A: So there is stuff that you do sometimes want in every single request. Essentially we're in a part of the workshop that talks about steering. We're just trying to steer Claude into, if you don't like something about what Claude is doing, you need some method of steering it and moving in the right direction. Claude, like proactive feeding that information to Claude, can be really useful so instead of it just finding it on its own, you're essentially pushing it to Claude.

Q: # So It's About Active Direction, Not Discovery

Right—so **steering** is the operative word here. You're not waiting for Claude to stumble into the right behavior. You're actively pushing it toward what you want.

That makes sense. But here's where I want to dig deeper on the philosophy:

**When Claude does something you don't like—and let's be concrete here—what kinds of things typically bother you?**

Is it like... style stuff ("you're using `var` instead of `const`")? Or is it more about approach ("you're modifying the database when you should be reading first")? Or workflow ("you're committing code without running tests")? 

In other words, **what are you actually steering *against*?** Because that shapes what belongs in Claude.md, right?

A: Essentially consistent code bases are happy code bases. If you notice something that the LLM is doing that is making your code base less consistent, you may want to steer it in a different direction. For instance, stuff that I have in my claude.md are things like:
- branch names
- patterns for commits
- methods for using tools that I like, like changesets and things like this

But really anything that you notice that you don't like about anything, anything you notice about the code, anything you notice about the way Claude is using your particular framework that you like, any opinions that you have, can be translated into a claude.md file.

Q: # So It's About Preserving Your Codebase's Identity

Okay, that's really insightful. So Claude.md is basically **a repository of your opinions**—the stuff that makes *your* codebase feel like *your* codebase, rather than some generic Claude-generated code.

Branch names, commit patterns, changesets... those are the little details that, if ignored, make a codebase feel "off." Like someone else walked in and did things their way instead of your way.

Here's the thing I want to probe on though: **How do you know when something is worth putting in Claude.md versus just... accepting that's how Claude works?**

Because I'm imagining a developer reading this thinking, "Well, I have *lots* of opinions about how code should be written. Should I just dump all of them into Claude.md?"

**What's the line between "this opinion matters for consistency" and "this is just me being picky"?** Is there one? Or is it more situational?

A: That's right. You should think about LLMs as having an instruction budget, as having a budget of different things that you can say to them that they will be able to remember. If you put every single one of your opinions inside Claude.md, what will happen is that the LLM, first of all, uses up tokens in your every single session that you use with Claude. If you have a huge Claude.md file that uses up even 3-4% of your context window, then that will push you further towards the dumb zone. You actually want to be pretty careful with the stuff that you put in the global scope that's in every single instruction.

Q: # The Token Tax Is Real

So there's a hard tradeoff here: **every opinion you put in Claude.md costs you tokens on literally every single request**, regardless of whether it's relevant to what you're asking Claude to do.

That's the discipline part, right? You can't just dump your entire coding philosophy in there.

**So here's the pragmatic question: how do you decide what stays and what goes?**

Like, you mentioned branch names, commits, changesets—those feel like they touch *most* of the work Claude does. But what about something more niche? Say you have really specific opinions about TypeScript interfaces versus types, or how you structure your test files. Does that still belong in Claude.md, or is that the kind of thing that belongs... somewhere else?

A: We'll talk about the different strategies for this later, like agent skills and stuff, but for now it's enough to say that you don't want to put too much in the AGENTS.md file. You do, however, do it as a crucial way that you can steer your LLM towards something that is a setup that you prefer.

Q: # Got It—The Philosophy Over The Tactics

Right, so we're staying at the 30,000-foot view here. The key insight is:

**Claude.md is your steering mechanism, but it's got a real cost, so you have to be intentional about what goes there.**

You don't need all the *how* yet—that comes later with skills and progressive disclosure. Right now it's just: *why* would you need to steer at all, and what's the tradeoff you're making?

Okay, so let me flip the question then: **Why do you *need* to steer Claude in the first place?**

Like, if Claude is a frontier LLM that's been trained on tons of code, why isn't it just... already doing the right thing? What's the gap between "Claude's default behavior" and "what you actually want"?

A: Claude has been trained to be a general-use LLM. It's used for tons and tons of different things and it has applications across the world and across many, many different industries.

You might think, "Oh I wish they would. I wish Anthropic would just train Claude to use interfaces not types; that would be great." It's incredibly expensive to basically reinforcement learning train to pre-train to bake that into the data. Training an LLM is an incredibly expensive process and so getting it to work at all is a minor miracle. Getting it to work on your specific use case would be an absolute sinkhole of money; would be required in order to get it done. All we're doing here is just spending a couple of tokens on most requests to steer it in the direction that we want. I think hoping that someday they encode that into the default behavior of the model is fanciful because Claude has to do so many different things.

Q: # Claude Is Generalist, You Need Specialist

That's the core tension right there. **Claude is built to work everywhere, which means it can't be optimized for *your* specific codebase, *your* conventions, *your* stack.**

So Claude.md is essentially the workaround—a cheap, token-efficient way to say "hey, in *this* context, here's what matters."

But here's what I'm curious about philosophically: **Does Claude ever *actively work against* you, or is it more that Claude is just... neutral?**

Like, is the problem "Claude keeps doing bad things I have to fix" or "Claude does *acceptable* things that just aren't *your* things"? Because those feel like different problems that might need different steering approaches.
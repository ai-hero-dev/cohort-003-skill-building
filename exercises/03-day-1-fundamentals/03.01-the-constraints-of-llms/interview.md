A: Go

Q: Hey! Great to have you here. So we're doing a pre-interview chat about **The Constraints of LLMs** — this is a solid topic with a lot of practical stuff in it.

Before we roll, I want to make sure we're on the same page about what you want to focus on. Let me ask:

**What aspects are you most excited to talk about?** Are you thinking:
- The technical nitty-gritty (attention scaling, KV cache, how it all breaks down)?
- The practical implications (how it affects your actual work with agents/coding)?
- A mix of both?

And here's what I'm seeing in the material — **a few angles that could make for interesting discussion:**

1. **The "smart zone vs. dumb zone" problem** — the idea that your LLM gets literally worse as you add more context. Super counterintuitive for people who assume "more data = better answers."

2. **Hallucinations as a feature, not a bug** — framing LLMs as lossy compressors makes this click for people. It's not that the model is broken; it's just how compression works.

3. **The statelessness problem** — why agents need structured context (system prompts, RAG, CLAUDE.md files) to actually remember anything meaningful between turns.

**What resonates with you?** Want to go deep on one of these, hit all three, or is there something else you want to lead with?

A: We're in the context of a coding course here. I want to make sure that by AI coding and specifically talking about Claude code, everything we talk about relates to that.

Q: Perfect — that's exactly the right lens. So we're grounding this in **practical Claude Code usage** for developers learning to work with AI.

Let me reframe those angles with that in mind:

1. **Context window management for coding tasks** — How do you structure your prompts/codebase context so Claude Code actually focuses on what matters? Why dumping your entire repo in the context is counterproductive.

2. **Hallucinations in a coding context** — Why Claude Code invents methods/libraries that don't exist, and how to prevent it (e.g., including relevant examples, pointing to actual implementations).

3. **Rebuilding context across turns** — Since Claude Code has no memory between sessions, how do you set it up so it can effectively work on the same codebase over multiple interactions? (This ties to things like agents.md, system prompts, structured notes.)

These all have immediate, actionable takeaways for someone learning to use Claude Code effectively.

**Does that feel like the right direction?** Should we focus on all three, or is there one of those that's most important for your students to understand first?

A: Yeah we're less talking about practical things in this section. We're mostly just talking about the constraints around what LLMs are and what they do. I kind of just want to talk about that and then talk about the applications of it a little bit later.

Q: Ah, got it — so this is **foundational knowledge first**, applications come later. Makes sense. We're building the mental model.

So we'd be talking about:

1. **Attention scaling and why it matters** — what's actually happening under the hood, the n² relationship problem, why more tokens = worse performance
2. **The smart zone / dumb zone** — where the model's attention actually works well vs. where it breaks down
3. **Hallucinations as lossy compression** — the taxonomy, why they happen, not a bug but a feature of how the tech works
4. **Statelessness** — no memory between conversations, blank slate every time
5. **Knowledge cutoffs** — what the model knows vs. what you need to feed it

Just the constraints themselves, explained clearly. The "okay, so how do I *use* this knowledge when I'm writing prompts for Claude Code" stuff comes in a different section.

That sound right?

A: Let's go live! Start the interview based on what we discussed.

Q: Awesome. Let's do it.

So I've read through "The Constraints of LLMs" and I'm thinking about how to break this down for developers who are new to working with Claude Code.

**Let's start here: Why do you think it's important for someone learning to use Claude Code to understand these constraints in the first place?** Like, what happens if they *don't* know this stuff?

A: A lot of people use the metaphor of AI and AI coding agents as like a junior developer who's come onto the team, who is very, very enthusiastic, can work 24/7, but needs to be steered and needs to be handled. I think the constraints on LLMs are even weirder than that and even more strange, even more outlandish.

What happens if you don't know those constraints is you start thinking of the LLM kind of like as a bad colleague and not understanding how they work best. Working with Claude, working with this coding agent, is going to be unlike any colleague you've ever worked with before. They're going to impose weird constraints on your system. They're going to make your code base; they're going to basically mean you need to improve your code quality at every turn. If you don't do that you're going to be really disappointed by what you get out of it. The substandard results that people tend to get when they don't know the constraints of LLMs mean they just end up with garbage code that's spat out. They blame the model or they blame the provider or they blame the harness, in this case Claude Code.

Q: That's really insightful — so it's not just "here's how LLMs work," it's **"here's why your expectations need to be different."** People come in thinking "this is a junior dev" and then get frustrated because it behaves nothing like a junior dev.

That makes me want to dig into the specifics. Let's take one of the constraints from the material — **the attention scaling problem**. 

In the document, there's this table showing how attention relationships scale quadratically — at 100,000 tokens you've got 10 billion attention scores per head. That's a wild number.

**When you're explaining this to someone learning Claude Code, what's the mental model you want them to walk away with?** Like, is it "more tokens = slower" or is it something deeper about *how the model actually degrades*?

A: So I think of the main constraints on these LLMs as the context window. As you say, every token that you add into the model is not just like adding a new character to a document or a new word onto the end of a document. If you just add a new character onto a document, it just gets longer and longer and that scales linearly in memory. You're just creating a long document.

When you add a new token to an LLM, the way it's stored in memory is it's not just storing the token; it's also storing that token and all of the relationships to every other token, which gets computed as a single number. You store a number for the token; you store a number for its relationship to every other token. That means that, instead of adding a character to a document, you're adding a team to a football league where the number of games scales quadratically because every other team has to play every other team. This means that this scaling relationship, as you add more tokens to the context as the conversation grows longer and longer and longer, puts way more strain on the LM than you might expect.

This means that LLMs kind of have a smart zone and a dumb zone. The smart zone is earlier in the context window where the attentional relationships are not so strained. You haven't put so much in the context and later on in the dumb zone you start seeing things like hallucinations come up more often. I tend to think about the smart zone/dumb zone as the main constraint with LLMs.

Q: Love that football league analogy — it immediately clicks why it's not just "the document got longer."

So if I'm following: the **smart zone/dumb zone split** is really the practical consequence of that attention scaling problem. Earlier in context = more attention budget per relationship. Later in context = stretched thin.

But here's what I want to understand better: **When you're working with Claude Code specifically, how does that actually *manifest*?** 

Like, if I'm a developer and I've got a 50,000 token conversation going with Claude Code, and we're deep in the "dumb zone" — what am I actually seeing happen? Am I seeing:
- More hallucinations (inventing methods that don't exist)?
- Worse reasoning (logical inconsistencies)?
- The model just forgetting what I told it earlier?
- Something else entirely?

What does a degraded Claude Code feel like in practice?

A: Yeah you're seeing more hallucinations, you're seeing worse reasoning. You're seeing it unable to find information that's in its context and it just ends up feeling crapper and you have to do a lot more steering.

In general a 50,000 token conversation is still pretty light. These models tend to have 200,000 token limits and so I think of it as around 80,000 tokens, where the context window starts to degrade and you end up kind of in the dumb zone. This is hugely debated. Different tasks might feel like you have a bit more window in the smart zone; it might be more like 60 or 70%. If you're pushing 80-90% then you're gonna definitely get a lot of degradation. No matter where the boundary is, everyone agrees that there is this problem with LLMs.

Q: Got it — so **80,000 tokens is roughly where things start to get weird**, and definitely by 80-90% of your context window you're in trouble.

That's a concrete threshold people can actually work with. And you're right — the research on this isn't perfectly settled, but the *existence* of the problem is universal.

Here's what I'm curious about though: **You mentioned that a 50,000 token conversation is "still pretty light,"** which suggests you can have multiple turns and still stay in the smart zone if you're careful. 

**So how do you actually manage that across a long session with Claude Code?** Like, are you:
- Periodically starting fresh conversations to reset the context?
- Actively pruning old context as you go?
- Something else to keep yourself from creeping into the dumb zone?

What does good context hygiene look like?

A: Yeah you're essentially clearing the context very often and quite aggressively in order to get back down but we'll talk about that later.

Q: Perfect — that makes sense, we'll circle back to the practical stuff.

So let's shift gears a bit. We've got the **attention scaling/smart zone problem** down. Let me ask about **hallucinations** — because the material frames them as something really specific: *lossy compression artifacts*.

**When you're explaining hallucinations to someone new to Claude Code, do you lead with that compression analogy?** Like, "LLMs are basically lossy compressors like JPEG or MP3" — or do you start somewhere else? Because that framing seems to fundamentally change how people *think* about the problem.

A: Yeah the other thing about this new colleague that you've taken on is that they have read, let's say, every publicly available document on the internet but they barely remember it. You can think of it like they've taken a photo of all of the world's knowledge but it's impossible for them to see it sharply. They see it extremely fuzzily so you really lossy compress information. They've taken all of the world's knowledge and they've compressed it down into a size that can run on a GPU and query that information on a GPU. That means that you can't use them as a database. You cannot ask an LLM a question and expect it to give you back an answer that's going to be reasonable because it only has a fuzzy recollection of everything it's seen.

Now you can augment that by giving LLM access to a knowledge base, let's say a code base. You can say OK produce some code that's like the code inside here, its memory inside its working memory, the stuff it can actually see in its context window. It remembers really well and it can produce really really well but stuff that it hasn't seen before or stuff that is barely seen or barely remembered then it's not going to do a good job on.

This is what we call a hallucination when Claude or any LLM basically just makes something up because it has an innate desire to serve you. This innate desire, which is often called sycophancy, often leads it astray because it wants to help so much that it ends up basically bullshitting until it finds an answer.

Q: That's really clarifying — so hallucinations aren't random errors, they're **the model trying so hard to help that it fills in the gaps with plausible-sounding nonsense.**

And the distinction you're making is crucial: **what's in the context window, the model sees sharply. Everything else is fuzzy.** So if you give Claude Code access to a library's actual code or documentation in the context, it'll work with that. If you ask it about something outside the context, it'll bullshit.

This connects directly to the taxonomy in the material — **factuality hallucinations** (making up facts) vs. **faithfulness hallucinations** (contradicting the context you gave it).

**Here's what I want to understand: When you're working with Claude Code on a real codebase, what's the most common hallucination failure you see?** Is it:
- Inventing methods/APIs that don't exist in a library?
- Getting the structure of your actual codebase wrong even though it's in context?
- Something else?

And more importantly — **is that hallucination preventable if you set things up right?**

A: I don't think making hallucinations preventable is the right way of thinking about it. It's more about making sure that you give the LLM the right context so that it's not relying on its own database, fuzzy compressed database of knowledge. Also giving it feedback loops so that when it does something wrong it is able to recover quickly and efficiently. Just like with humans really.

Q: That's a really important distinction — it's not "eliminate hallucinations," it's **"design the system so the model isn't forced to rely on fuzzy knowledge in the first place."**

And then **feedback loops** so when it does go off the rails, it can correct course quickly instead of compounding the error.

That feels like it's starting to bridge toward the application side, which we'll dig into later. But let me stay in the constraints space for a moment.

The material mentions **statelessness** — the idea that LLMs have zero persistent memory between conversations. Every new conversation is a blank slate.

**How big of a problem is that for someone using Claude Code?** Like, is it just an inconvenience, or does it fundamentally change how you have to structure your entire workflow with the tool?

A: Statelessness is the other main constraint about LLMs because every time you start a new conversation, the model forgets everything that it had previously understood because you're essentially just resetting all of its working memory. Now this means it's kind of like the guy from Memento (which is a great quote out there). Memento is a movie about context engineering. The guy from Memento, I honestly can't remember the plot, but he has some sort of insomnia where he forgets everything that he previously remembered. He leaves these tattoos on his own body of everything that he needs to remember in order to make it through the day and this is kind of like how you need to treat LLMs. They are the guy from Memento.

I think a better analogy is that every time you start a conversation with an LLM, it's like it's a new starter to your code base. This imposes a lot of constraints on your code base. Is your code base friendly to new starters? Every 20 minutes or every time you reset the conversation with the LLM, it's going to be a new starter on your code base. Can it get up and running quickly? Is the documentation easy to find, easy to reference? Is the code easy to read? Are related pieces of code grouped together?

These are all things you need to think about when you put this constraint of using AI coding agents on your code base.

This is, I think, something that lots of devs kind of get wrong or they have too high expectations of AI. They think AI is going to develop a working memory of their code base and is going to act like a programmer. Because AI doesn't really have a human programmer, they can handle a bad code base because they will just hit their head against the wall again and again and again until they learn the things that can go wrong in the code base and start to work around them.

In other words human developers are stateful but LLMs are totally stateless. This means that LLMs have this new starter constraint that puts a lot of constraints on your code base and how you treat the LLM.

Q: That's a *really* sharp insight — **statelessness isn't just a limitation of the model, it's a constraint on your codebase.** Every reset is a new onboarding. Can your repo onboard someone (or something) quickly and effectively?

So the Memento/new starter framing makes it crystal clear: if your codebase is a mess, a human developer will eventually figure it out through repeated failure. Claude Code can't. It just resets and encounters the same mess again.

This feels like it's starting to touch on the broader picture, so let me ask:

**Of the three big constraints we've talked about — attention scaling/smart zone, hallucinations from lossy compression, and statelessness — which one do you think surprises people the most when they first learn about it?** 

Or put another way: **which constraint do you think people most underestimate when they start using Claude Code?**

A: Let's go next question.

Q: Got it. Let me ask about **knowledge cutoff dates** — the last constraint in the material.

So the idea here is: the model was trained on data up to a certain date, and anything after that is invisible to its "parametric knowledge" (the stuff baked into the weights). But you *can* feed it new information via context.

**For someone using Claude Code, how much should they actually worry about this?** Like, is it:
- A real problem if you're working with older, stable frameworks?
- A massive problem if you're using cutting-edge libraries?
- Something that just requires you to always include relevant docs/examples in your context?

What's your take on how much this matters in practice?

A: Yeah this is a problem with the way that LLMs compress information. Not only have they seen all the material in the world, have they compressed it down into a really fuzzy jpeg? It's also got a really severe cut-off date. At the time that the model is shipped, it's extremely expensive to train a model and compress down this png or jpg of all of the world's information. That's an expensive process and they have to stop at some point. The model might not have access to data that you need.

If your library that you depend on has released a new major version then the knowledge that the model innately has access to and that it sort of vaguely understands might not be available to it. This means that if you need specific information that the model doesn't know or hasn't seen because it was released a few months ago, then you need to provide that information. This is another reason why you really can't use LLMs as a database.

Q: Right — so **knowledge cutoff is another reason why you can't just ask the model questions and expect good answers.** It's not just fuzzy compression, it's also time-gated.

That ties back to what you said earlier about **giving the model the right context so it's not relying on its fuzzy, outdated knowledge.** If your library shipped a new API after the training cutoff, you have to put that in the context window or the model will hallucinate.

Let me zoom out for a second. We've covered:
- **Attention scaling / smart zone degradation**
- **Hallucinations as lossy compression artifacts**
- **Statelessness**
- **Knowledge cutoff dates**

**Is there anything about these constraints that you think is really counterintuitive or that people get fundamentally wrong?** Like, something that breaks people's mental model of how LLMs work?
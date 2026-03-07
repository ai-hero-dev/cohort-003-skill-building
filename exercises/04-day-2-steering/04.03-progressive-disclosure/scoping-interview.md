A: So I want to scope this. This is a nice lesson because we're really explaining a concept that's then going to recur through the rest of the course. It's a quite pivotal lesson and it focuses just purely on the concept of progressive disclosure. We're going to use an agents.md file, which I've pasted in. And we're going to talk about how you might structure this so that it's better for the agent to read. Essentially the solution to that is progressive disclosure. You don't want to present everything kind of in one place; you want to just show the user what they need and then give them a map for how to get more information. This is a famous UI concept, progressive disclosure of complexity. You show them just enough and then show them how to get more and this will then be pulled into the next thing we talk about, which will be skills.

We also want to touch on the fact that progressive disclosure can be related to code-based structure too, to the way the file system is designed, to even the way you design interfaces. Although maybe we should just give that throwaway mention and properly touch on it later.

Q: I'm going to push back a bit here, and I think you'll see why once I articulate it.

Looking at the course structure, I see **03.02-steering-an-agent-with-the-agents-md-file** comes right before this lesson, and **03.04-what-are-agent-skills** comes right after. 

Here's my read: You've got a **concept lesson** (this one) that's genuinely foundational and will recur throughout the course. That's valuable. But I'm seeing potential scope creep already in your description.

**Here's my concern:**

You're describing three things:
1. **The core concept**: Progressive disclosure (what it is, why it matters, the classic UI principle)
2. **How it applies to AGENTS.md files specifically** (the structure, the pattern, the "what to put where")
3. **How it applies more broadly** (code structure, filesystem design, interfaces) — even as a "throwaway mention"

That third one is the problem. Even a throwaway mention is scope creep, because:
- It dilutes the focus from the core takeaway
- It sets up future lessons but doesn't deliver on *this* lesson's promise
- The learner will finish thinking "so... how does this apply to my actual code structure?" and that question doesn't get answered

**My recommendation:**

Keep this lesson **ruthlessly focused on progressive disclosure as a mental model + how it applies to AGENTS.md files**. The AGENTS.md you've pasted in is perfect — it's a concrete, tight example. The learner should finish this lesson with one clear skill: **"I can recognize where an AGENTS.md file is trying to show too much, and I can restructure it using progressive disclosure principles."**

The broader "progressive disclosure in filesystem design, interfaces, etc." should either:
- Be its own lesson later (maybe in the advanced patterns section?), or
- Come up naturally when you teach skills in 03.04, where you'll probably say "here's where we apply the same principle to skill organization"

**Questions for you:**

1. **What's the single takeaway?** After this lesson, should the learner be able to: *"Apply progressive disclosure to an AGENTS.md file by identifying what's essential vs. supporting context, and restructuring accordingly"?* Or is it something broader?

2. **How much time are we spending on the broader concept vs. the AGENTS.md application?** If it's more than 20% of the lesson on the broader stuff, that's a sign it should be its own thing.

3. **Does 03.04 (skills) expect the learner to already understand progressive disclosure as a general principle**, or does it re-teach it in the context of skills? (This matters for how much time we spend on theory here vs. application.)

A: 304 expects the learner to understand progressive disclosure as a general principle. The stuff about it being useful more broadly is kind of just a throwaway sentence, I think. In this overall thing we're framing this concept as something that can be useful more widely but really what we're doing is teaching it in the context of steering and Agents.md and Skills.

Q: Perfect. That changes things significantly — and actually makes the scope **tighter**, not broader.

So if 03.04 expects learners to already understand progressive disclosure as a general principle, then **this lesson needs to teach the principle itself**, using AGENTS.md as the concrete vehicle. Not the other way around.

That means:

**The core takeaway should be:** *"Progressive disclosure is a design principle where you show only essential information upfront and provide a map to deeper details. It makes complex systems easier to navigate."*

And AGENTS.md is just the teaching example — the context where we illustrate this principle at work.

**Here's what I'm thinking for scope:**

**IN SCOPE:**
- What progressive disclosure is (the principle itself, briefly grounded in UI/UX history so it's not abstract)
- Why it matters for agents reading your AGENTS.md (cognitive load, signal-to-noise, etc.)
- How the AGENTS.md you've pasted demonstrates (or fails to demonstrate) progressive disclosure
- The pattern: essential rules first, details after, clear signposting

**OUT OF SCOPE:**
- How to apply it to filesystem/code structure (even throwaway — save for later when it comes up naturally)
- Deep dive into skills-specific progressive disclosure (that's 03.04's job)
- How to write the "map" itself (like, "here's how to structure your signposting" — that's implementation detail for skills)

**One clarifying question before we lock sequence:**

Looking at that AGENTS.md file you pasted — is it a *good* example of progressive disclosure (teaching by showing what's done right), or is it a *bad* example that needs fixing (teaching by diagnosis)? Or does it mix both?

That changes how we structure the lesson's arc.

A: It's a bad example that needs fixing essentially.

Q: Excellent. That's a much stronger teaching move.

So the arc becomes: **Here's the principle → Here's what happens when you violate it → Here's how you fix it.**

That's pedagogically sound because the learner sees the *problem* before they see the *solution*, which makes the solution land harder.

**Before I lock the sequence, one more thing I need to understand:**

In your lesson, are we actually going to **rewrite that AGENTS.md together** (showing the before/after, reorganizing it), or are we just going to **diagnose what's wrong with it** and let the learner infer how to fix it?

Because that determines a lot:
- If we rewrite it: the lesson is longer, more hands-on, learner leaves with a concrete template they can copy
- If we diagnose: the lesson is tighter, more conceptual, learner leaves understanding the principle but has to apply it themselves (which is fine if 03.04 is going to ask them to do exactly this with skills)

Which feels right to you? And does it align with the difficulty/pacing you want at this point in the course?

A: This is a knowledge-based lesson. We're going to essentially diagnose it and maybe draw some diagrams for groupings of ideas, groupings of things that might be in there. We could group them into a tree structure instead of a single monolith.

Q: Got it. **Knowledge-based, diagnostic, with visual aid (tree/grouping diagrams).** That's clean and it respects the learner's intelligence — you're teaching them to *see* the problem, not hand-feeding them the solution.

That also means this lesson is **explicitly setting up for 03.04**, where they'll apply this same diagnostic lens to skills.

One final scope clarification before I give you the summary:

**The AGENTS.md you've got — should the learner understand *why* each rule is grouped the way it is?** Or are the diagrams just showing "here's how this could be reorganized" without necessarily committing to a specific grouping scheme?

In other words:
- Do we teach *what makes a good grouping* (e.g., "database conventions go together because they're all about persistence layer"), or
- Do we just show *that grouping is possible* and let them develop taste as they go?

This matters because it affects whether we're teaching a principle (grouping by domain/concern) or just a technique ("you could arrange it differently").

My instinct: You want to teach the **principle** — that progressive disclosure is about grouping by relevance/need — because that principle will transfer to skills, filesystems, etc. But I want to confirm that's the depth you're going for.

A: I think we show them that grouping is possible and will develop taste later.

Q: Perfect. That's the right call — it keeps this lesson focused and lets taste develop naturally through 03.04 and beyond.

Okay, I'm ready to lock scope and sequence. Let me make sure I have this right before I write the summary:

**One final confirmation on the teaching sequence:**

I'm imagining:
1. **Start with the principle** — what is progressive disclosure (the UI/UX concept, brief and clear)
2. **Why it matters for agents** — cognitive load, signal-to-noise ratio, what happens when it's violated
3. **Diagnosis** — walk through the AGENTS.md example and identify where it's doing too much at once
4. **Visualization** — show what regrouping could look like (tree/grouping diagrams) without prescribing a single "right" way
5. **Close with the payoff** — this principle will come up again (skills, and beyond)

Does that sequence feel right? Or would you reorder anything?

A: I think instead we're going to pick up where we left off and essentially show them this claude.md file, then go into why it's bad, then go into how we might want to restructure it. We then say, okay this concept actually has a name; it's progressive disclosure and it's useful much more widely. We then close with the payoff.

Q: Ah, I like that better actually — **start concrete, then name the pattern, then abstract out.**

That's stronger pedagogy than starting with definition. You show them the problem first, they feel the friction, *then* you give them the concept that explains it. Way more satisfying.

So the sequence is:
1. **Here's the AGENTS.md** — dump the code, let them see it
2. **Why it's bad** — diagnose the problems (what's overwhelming? what's signal vs. noise?)
3. **How we might restructure** — show grouping/tree diagrams of alternative organizations
4. **Name the principle** — "this is called progressive disclosure, and here's why it matters"
5. **Payoff** — you'll see this pattern again (skills next, and beyond)

One micro-question on #4: When you name the principle, do you want to give a quick definition/brief history of where it comes from (UI/UX design), or just name it and explain why it's useful in *this* context?

I'm leaning toward: **name it + explain why it matters for agents**, skip the UI/UX history. Keeps momentum, respects the learner's time, and the "why" is what matters here.

Does that track?

A: I think just one sentence about UI/UX history.

Q: Perfect. One sentence, then pivot to why it matters for agents. Got it.

**I'm ready to write the scope summary.** Last thing — just need confirmation on one detail:

When you show the "how we might restructure it" section with diagrams/groupings — are we showing *one* reorganization as an example, or *multiple possible ways* to group things to show there's no single "right" answer?

I'm thinking one example is cleaner and less confusing, but I want to make sure that aligns with your intent of "developing taste later."

A: I think one example.

Q: Done.

---

**Scope Summary**

**Lesson title:** Progressive Disclosure

**Core takeaway:** Progressive disclosure is a design principle where you surface only essential information upfront and provide a map to deeper details—making complex systems easier to navigate.

**Prerequisites:** 
- Understanding of what an AGENTS.md file is and its role in steering agents (from 03.02)
- Familiarity with the specific AGENTS.md code example provided

**In scope:**
- Analyzing the provided AGENTS.md file and identifying where it violates progressive disclosure (cognitive overload, signal-to-noise ratio issues)
- Demonstrating how to restructure an AGENTS.md file using progressive disclosure (one concrete example with diagrams/tree groupings)
- Naming the principle and briefly grounding it in UI/UX design history (one sentence)
- Explaining why progressive disclosure matters specifically for agents reading your instructions
- Signposting that this principle will recur (skills in 03.04, and beyond)

**Out of scope:**
- How to apply progressive disclosure to filesystem structure, code interfaces, or broader codebase design (save for later lessons where it comes up naturally)
- Teaching "taste" in grouping—that develops through application in 03.04 and beyond
- Prescribing a single "correct" way to organize information (one example is enough)
- Implementation details of how to write signposting or maps (that's skills' responsibility)

**Teaching sequence:**
1. **Show the problem first** — Present the AGENTS.md file as-is so learners see the cognitive load upfront
2. **Diagnose the friction** — Walk through what makes it hard to read (everything at once, no hierarchy, unclear what's essential vs. supporting)
3. **Show one restructuring** — Demonstrate how regrouping with tree/diagram visualization makes it clearer (one concrete example)
4. **Name and ground the principle** — "This is called progressive disclosure, a UI/UX principle that..." (one sentence) + why it matters for agents
5. **Close with payoff** — This pattern will come up again (skills next, and throughout the course)

---
A: Go

Q: Looking at what we've got:

**Context snapshot:**
- This lesson sits in **Day 2: Steering** — right after learners understand what an `agents.md` file is (02.01) and how to use it to steer agents (02.02)
- The next lesson is **02.04: A Skill for Writing Skills** — which sounds like it's about building or refining skills themselves
- The course trajectory: fundamentals → steering → planning → feedback loops → autonomous agents → advanced patterns
- The placeholder content says: "Understand the difference between user-invoked skills and agent-invoked skills. Learn how skills extend agent capabilities."

**My initial read:** This lesson is about **what skills are and how they work as a steering mechanism** — not how to build them (that's 02.04). The takeaway feels like it should be: *"A skill is a reusable instruction set that either a user can trigger or an agent can self-invoke, and knowing the difference changes how you write your agents.md file to steer agent behavior."*

But before I go further, I need to clarify some things:

1. **What's the gap the learner feels?** After 02.01 and 02.02, they know *agents.md exists* and *how to write it*. What do they NOT understand yet about steering that "skills" solves for? Is it "I don't know how to make agents do specific things repeatedly" or "I don't know how to prevent agents from doing things they shouldn't"?

2. **How much does this lesson overlap with 02.04?** If 02.04 is "A Skill for Writing Skills," does that mean 02.04 teaches them how to *create* a skill to help them write skills better? If so, 02.03 should just explain the *concept* of skills, not how to build them, right?

3. **What counts as a "skill" in this course?** Is it a specific tool/MCP, a prompt pattern, an agents.md directive, or something else entirely?

Give me those three things and I can help you draw tight boundaries around this lesson.

A: So I think the gap that they now feel is what happens when your agents.md file grows really, really big and overwhelmingly large. How do you break that down into things that you can reuse across your team. The main thing, the main benefit that skills bring, is that progressive disclosure is baked into them. Only the name and description of the skill are given to the LLM. The LLM can invoke it itself by just running /the skill name. When it does that, it shows the entire skill.md file. From there you can even include progressively disclosed stuff within that too.

Agent skills are an open standard invented by Anthropic but given away to an open foundation, as far as I understand it. Skills do help to solve the problem of massive agents.md files. You can break down those agents.md files and then the agent can just pull it in when they need it.

Q: Okay, this is **much** clearer and actually pretty elegant. Let me reframe:

**The real problem being solved:** Your agents.md file becomes a cognitive overload for the LLM. By the time you've written comprehensive steering for 10+ behaviors, the agent has to parse all of it every context window. Skills solve this with **lazy loading** — the agent only gets the detailed instruction when it actually needs to invoke that skill.

**The progressive disclosure angle is key** — the agent sees `skill-name: description` in agents.md, but the full skill.md only loads on invocation. That's genuinely clever.

So here's my read on scope:

This lesson should teach **the conceptual difference between monolithic agents.md and decomposed skills, and how that changes what the agent can do**. NOT how to build skills (that's 02.04). NOT the technical plumbing of how MCPs work or how to wire them up.

But I have two clarifying questions before we lock scope:

1. **User-invoked vs. agent-invoked** — your placeholder mentions this distinction. Does that matter for *understanding* what skills are? Or is that an implementation detail that belongs in a "how to build skills" lesson? (I'm guessing the agent-invoked part is the core insight here, and user-invoked is secondary.)

2. **Hands-on expectation** — does the learner need to *see* a skill in action in this lesson? Like, watch Claude invoke a skill and show the progressive disclosure? Or is this more of a conceptual "here's why this matters" lesson where they then *build* one in 02.04?

Those answers will tell me if this is a tight 15-minute conceptual lesson or if it needs worked examples.

A: Yeah I don't think we care about MCPs here. It's out of scope. I think we want to explain what this is, more knowledge, and then the next thing is going to be 0.2.04, which is going to be skills essentially. There's no hands-on expectation here. We're just explaining the concept of skills and then the next exercise you're going to get hands-on.
I think (this is my personal take on skills) that there are two types of skills really:
1. Agent-invoked skills that you can use to guide the agent's behavior
2. User-invoked skills. These are skills that you kind of have sitting around in your Claude Code setup to invoke, like to change the agent's behavior
This is where you might want to get it to write a PRD or something or, I have some for TDD, for a refactor plan. We're going to look at some of those later on. It's more a how skills are used in the real world really.

Q: Perfect. This is now **crystal clear** and I'm going to push back slightly on one thing, then confirm scope.

**The push-back:** You're describing two *uses* of skills (agent-invoked vs. user-invoked), but they're the same *thing* technically — a reusable instruction set with progressive disclosure. I think the lesson should emphasize that **the architecture is identical; the difference is just who triggers it and why**.

Here's why: If you conflate "type of skill" with "how it's used," the learner might think they're building two different objects in 02.04. They're not. A skill is a skill. The user-invoked examples (your TDD skill, the refactor plan skill, the PRD skill) are just skills that *happen to be useful when a human decides to invoke them*, not because they're structurally different.

**That said, I think this is the right framing for the lesson:**
- **Why skills exist:** Agents.md gets unwieldy. Skills break it into reusable, progressively-disclosed chunks.
- **How they work:** Agent sees the name + description in agents.md. When it (or a user) invokes the skill, the full instructions load.
- **Two use patterns:** Agent-invoked (agent decides "I need this skill to do my job") vs. user-invoked (human says "run this skill to change how the agent behaves").

This is **purely conceptual and knowledge-based** — no hands-on work, no building. Just "here's what skills are and why they matter."

Does that land? And one final question: **Do we need to show ANY concrete examples** (like "here's what a skill.md file looks like") or keep it purely abstract?

A: There's also distribution as well. Skills are really easy to package and distribute across your whole organization. This is something that people are still trying to figure out but the idea of skills just literally being a folder in the file system means they're super simple to distribute across an org or even open source like on skills.sh. I think probably we do need one concrete example of what a skill looks like. Maybe even we take the example of positional parameters from the previous example or the previous lesson and we turn that into a skill. I can't remember what the next lesson actually covers; maybe we'll do that in the next lesson.

Q: **Okay, now I've got it.** Skills aren't just about progressive disclosure — they're also about **portability and shareability**. That's a huge part of the value proposition.

One concrete example makes sense. And I like your instinct about potentially reusing something from 02.02 (the steering lesson) — it gives continuity and shows "this thing you just learned to put in agents.md can be extracted into a reusable skill."

But let me check: **Do we know what 02.04 covers yet?** You said "A Skill for Writing Skills" — does that mean:
- Building your first skill from scratch?
- Building a skill that helps you write better skills (like a meta-skill)?
- Something else?

This matters because if 02.04 is "build a skill," then 02.03 should show a *simple* skill example (maybe the positional parameters thing, maybe something even simpler) just to demystify the format. Not build one, just show one.

But if 02.04 is "build a meta-skill for skill-writing," then maybe we want a slightly richer example in 02.03 so learners can see the full possibility space.

What's the actual scope of 02.04? That'll tell me how much detail the example in 02.03 needs.

A: The scope of O2O4 is we use a skill that I've written to write a skill, basically. It sort of teaches both angles in a funny way. It's a really useful skill for people to take away and just use themselves.

Q: **Ah, beautiful.** So 02.04 is a meta-lesson where learners use a *pre-built skill* (one you've written) to create their own skill. They learn by doing, using a tool that makes skill-writing easier. And they walk away with both the skill they created AND your reusable skill-writing tool.

That means **02.03 should be very light on concrete examples.** You just need enough to demystify the format — show that a skill.md is not some mysterious thing, it's just a folder with clear structure. The learner doesn't need to understand how to build one yet; they just need to not be intimidated by it.

**Here's my read on final scope:**

---

**Scope Summary**

**Lesson title:** What Are Agent Skills?

**Core takeaway:** Skills are reusable, progressively-disclosed instruction sets that solve the agents.md bloat problem and distribute easily across teams — an agent (or user) invokes them by name, and only then does the full instruction load.

**Prerequisites:** 
- Completed 02.01 (what agents.md is) and 02.02 (how to steer with agents.md)
- Understanding that large agents.md files become unwieldy

**In scope:**
- The problem skills solve: agents.md cognitive overload for the LLM
- How progressive disclosure works: agent sees name + description; full skill loads on invocation
- Two invocation patterns: agent-invoked (agent decides) vs. user-invoked (human decides)
- Distribution benefit: skills as shareable, portable folder structures across orgs/open source
- One simple, concrete example showing the format (just enough to demystify, not to teach building)

**Out of scope:**
- How to build a skill (that's 02.04)
- MCPs or technical infrastructure
- Hands-on creation or exercise
- Advanced skill patterns or nested progressive disclosure

**Rough flow:**
1. Open with the pain point: large agents.md files become cognitive overload for the LLM
2. Introduce skills as the solution: name + description in agents.md, full instruction on invocation
3. Explain progressive disclosure: why this matters for agent performance
4. Show the two invocation patterns: agent-driven vs. user-driven, with brief examples of each use case
5. Add the distribution angle: skills as shareable, portable artifacts
6. Show one simple skill example: just the structure and format (demystify, don't teach building)
7. Close with: "In the next lesson, you'll use a skill-writing skill to build one yourself"

---

Does this feel right, or should we tighten/adjust anything?
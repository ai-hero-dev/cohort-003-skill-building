A: This is a skills-based lesson. The kind of intro here is understanding that frontend is really hard for AI. The user will walk in with a PRD to build a feature and the repo will be ready for them with Playwright MCP already set up. The idea here is that we want to try to get the most out of Playwright MCP by building a frontend feature using it. There's not a huge amount of knowledge that needs setting up here.

This is the first time we've encountered the idea that frontend is harder for agents than backend but I don't feel like that's a big enough juicy nugget that it needs to be in its own lesson.

Q: Okay, I'm reading the context now. Let me ground myself:

**Where this sits**: You're in Day 4 (feedback loops), and you've just come from 04.06 (what makes a good test). The learner has spent the course learning how to steer agents, plan massive tasks, and build feedback loops into their workflows. Now they're hitting a real constraint: **frontend work is fundamentally harder for agents than backend work**.

**What comes next**: Day 5 is Ralph (autonomous multi-step execution), so this lesson needs to demonstrate what agents *can* do with proper tooling and feedback loops before handing them off to Ralph.

Here's my take on your instinct: **You're right that "frontend is hard" doesn't deserve its own lesson, but it's a critical *framing* for why we need Playwright MCP in the first place.** That framing should live in the intro, not consume the lesson.

**Now let me probe the actual scope:**

1. **What's the ONE thing the learner should be able to do after this lesson?** Is it:
   - "Use Playwright MCP to build a frontend feature from a PRD"?
   - "Know when/how to lean on Playwright MCP to compensate for agent limitations"?
   - "Integrate Playwright MCP into their feedback loop workflow"?
   
   These are subtly different. Which one matters most?

2. **The repo comes pre-configured with Playwright MCP already set up.** That's smart — no setup friction. But does the learner need to understand *what* Playwright MCP is and *why* we're using it, or can they just "here's the tool, now use it"?

3. **The skill angle**: The description mentions "add it to the Red Green Refactor skill from the previous exercise." Is the main output here that they:
   - Extend their RGR skill to incorporate Playwright testing?
   - Build a new frontend-specific skill that uses Playwright MCP?
   - Something else?

What's your vision for what the learner walks away *doing*?

A: I think integrating player MCP into their feedback loop workflow is the most important. The learner needs to understand what player MCP is but it's not that hard to understand. The skill angle is that it will be added for them. I don't think we'll need to integrate Red Green Refactor into this one so it's more like, previously in this section, they will have built a skill that just runs the feedback loops without doing RGR because we're not necessarily writing tests for frontend. Frontend testing is a little bit tricky. We're going to instead be validating that it works with Playwright.

Q: **This is landing for me now.** Let me reframe what I'm hearing:

The learner has just built a feedback loop skill (without RGR, because frontend doesn't lend itself to TDD the same way). Now they're walking into this lesson with:
- A PRD for a frontend feature
- A repo with Playwright MCP already configured
- Their existing feedback loop skill from the previous lesson

**The core takeaway**: Use Playwright MCP to validate that your frontend implementation actually works — this *is* your feedback loop for frontend work.

That's clean. It's a direct answer to "how do we close the loop on frontend features when TDD doesn't fit?"

**But I need to clarify one boundary, because it affects scope:**

When you say "validating that it works with Playwright" — are we talking about:

**Option A**: Writing Playwright tests/assertions that the agent runs to check "does the UI match the PRD?" (the agent uses Playwright MCP to verify its own work)

**Option B**: The learner using Playwright MCP interactively to check the agent's work, then feeding that back into the loop

**Option C**: The agent proactively using Playwright MCP to explore the UI, validate behavior, and self-correct

I think this distinction matters because it affects *how much* the learner needs to understand about Playwright syntax vs. just understanding "this is how agents validate frontend work."

What's your vision — is the agent writing Playwright code, or is Playwright MCP more of a sensory tool the agent uses to see what it built?

A: Playwright MCP will just be checking the agent's work and feeding that back. The agent will be using Playwright MCP itself to check its own work, kind of like a frontend developer would. We are not actually writing any Playwright tests here.

Q: **Perfect. That's a clean boundary.**

So the agent is using Playwright MCP as a **sensory tool** — it builds the feature, then uses Playwright to poke at it and see if it matches the PRD. If it doesn't, that feedback loops back and the agent iterates. No test writing, no assertions in code — just interactive validation.

This means the learner doesn't need to understand Playwright syntax deeply. They need to understand:
- What Playwright MCP can *do* (navigate, interact, inspect the DOM)
- How to steer the agent to use it as a validation step
- What to look for when the feedback comes back

**Now here's my scope concern:**

This lesson could balloon in two ways:

1. **"Here's everything Playwright MCP can do"** — screenshot, click, fill forms, inspect selectors, etc. That's a rabbit hole.
2. **"Let me set up the skill perfectly"** — getting the agent to reliably use Playwright, handle edge cases, etc.

**I'd push back on both.** Here's what I think should be IN scope:

- Build a frontend feature from the PRD
- The agent uses Playwright MCP to validate the feature works
- When validation fails, the feedback loops and the agent tries again
- The learner observes this cycle and understands why it works

**What should be OUT of scope** (deliberate):
- Deep Playwright API documentation (just enough to understand what's happening)
- Optimizing the skill for production use
- Handling complex edge cases in the validation loop
- Writing custom Playwright scripts (the agent drives this, not the learner)

Does that feel right? Or am I being too narrow?

A: Yep that sounds good. I don't think they're going to be doing too much skill fiddling. It's more like let's have a go with Playwright MCP and see how it works.

Q: **Good.** So this is fundamentally an **experiential lesson**, not a skill-building one. The learner is *using* Playwright MCP as a tool, not *engineering* it.

That changes the teaching shape significantly. Let me propose the sequence:

**Teaching sequence:**

1. **Why frontend is different** — Quick framing (maybe 1-2 minutes). Backend has tests, logs, clear success criteria. Frontend is visual and interactive. Agents struggle with this. Playwright MCP gives agents *eyes*.

2. **What Playwright MCP can do (for validation)** — Show 3-4 concrete examples: "navigate to the page," "click this button," "check that the text appears," "verify the layout changed." Not exhaustive. Just enough that they see the pattern.

3. **Set up the scenario** — Here's your PRD, here's the repo with Playwright MCP ready. Your skill from the last lesson will handle the loop. Claude will use Playwright to validate.

4. **Watch it work** — Build the feature. Show the agent using Playwright mid-build to check "did that button appear?" Fail, iterate, succeed.

5. **Reflect on the loop** — This is your feedback loop for frontend. No tests. Just: build → validate with Playwright → iterate.

**The key question for pacing:** How hands-on is this? Are they:
- Watching a walkthrough of the agent building a feature?
- Actually building a feature themselves with a PRD?
- Both (guided build, then try their own)?

That affects how much time we need and what the lesson structure looks like.

A: Nah this is super hands-on.

Q: **Excellent.** That's the right move for a skills lesson.

So the learner is actually *doing* it — building a real frontend feature, seeing the agent use Playwright MCP to validate, dealing with failures, watching it iterate.

That means the lesson structure is probably:

1. **Very quick framing** (why frontend is hard, why Playwright MCP matters)
2. **Here's your PRD and your repo** (get them oriented fast)
3. **Go build it** (they prompt the agent, agent builds, agent uses Playwright to check, feedback loops)
4. **What did you notice?** (reflection on what worked, what didn't, how the validation loop felt different from backend)

**But here's what I need to know to finalize scope:**

**How much should we prep them for failure?** Playwright MCP validation might:
- Work flawlessly (agent builds, validates, done)
- Get stuck in a loop (agent builds something, Playwright says it's wrong, agent tries again, fails again)
- Miss the PRD entirely (agent builds confidently but it's not what was asked)

Should this lesson include **troubleshooting guidance**? Like "if the agent keeps failing validation, try X"? Or is the lesson just "here's the tool, go use it" and we let them experience the friction?

Because *that* answer determines whether we keep this tight and focused or whether we need to add a debugging/fallback section.

A: Yeah I think some light troubleshooting guidance but not a huge amount. They will have the Discord that they can use to jump into if they run into trouble here. Honestly just sort of trying to fight with the agent is always good learning material.

Q: **Perfect.** Light troubleshooting, then "jump to Discord if you're stuck." That's honest and realistic.

Okay, I think we've got enough to lock this down. Let me propose the final shape:

---

**Scope Summary**

**Lesson title**: Building Frontend Features with Playwright MCP

**Core takeaway**: Use Playwright MCP to validate frontend features during development — this is how agents close the feedback loop on visual/interactive work.

**Prerequisites**: 
- Completed 04.06 (what makes a good test) — specifically, understanding feedback loops
- Built a feedback loop skill in the previous lesson (04.05 or similar)
- Basic understanding of PRDs and feature requirements

**In scope**:
- Why frontend validation is harder for agents than backend (brief framing)
- What Playwright MCP does as a validation tool (navigate, interact, inspect, verify)
- Building a real frontend feature from a PRD using Claude Code
- Watching the agent use Playwright MCP mid-build to validate its work
- Experience the feedback loop: build → validate → iterate → succeed
- Light troubleshooting when validation fails (why is the agent stuck? what signals should you look for?)

**Out of scope**:
- Deep Playwright API documentation or syntax
- Writing Playwright tests or assertions in code
- Optimizing or refining the skill for production
- Complex edge cases or advanced validation patterns
- Setting up Playwright MCP (repo comes pre-configured)

**Teaching sequence**:
1. **Why this is different** — Frontend is hard for agents because it's visual/interactive; tests alone don't cut it. Playwright MCP gives agents a way to *see* and validate their work.
2. **What Playwright MCP can do** — Show 3-4 concrete validation moves: navigate, click, verify text appears, check layout changed. Emphasize this is for validation, not test-writing.
3. **Get oriented** — Here's your PRD, here's your repo (already set up), here's your feedback loop skill. Go.
4. **Build and validate** — Prompt Claude to build the feature. Let them watch as Claude uses Playwright to check if it works. Fail, iterate, succeed.
5. **Light troubleshooting** — If the agent gets stuck validating, here are some signals to look for (is it validating the wrong thing? misunderstanding the PRD? looping endlessly?). When in doubt, Discord.
6. **Reflect** — What felt different about this feedback loop vs. backend work? How did Playwright validation help the agent self-correct?

---

**Does this lock it?** Anything you'd reorder, expand, or cut?
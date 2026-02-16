A: So this lesson is basically just about understanding something that they might have noticed in the previous lesson when we're using human in the loop. Ralph is the degree to which Claude pings them for permissions requests and in order to run autonomously we need to be an environment where those permissions requests are handled automatically.

Now this might end up being basically the fix for that is to use docker sandboxes and docker sandboxes are basically a prerequisite for using Ralph so that's what we're gonna be doing: setting up Claude code within a docker sandbox. I'll show you; it's a little bit awkward to do it but it's well worth it for Ralph. This sets up the next lesson, which is all about afk Ralph and there's not much to it really.

Q: Okay, I'm reading this carefully and I think I see what you're trying to do — but I need to push back on the framing a bit, because it's affecting scope.

Let me ground myself in the course structure first:

- **05.02** (HITL Ralph) — learner just experienced Ralph pinging for permissions
- **05.03** (this lesson) — sandboxing setup
- **05.04** (AFK Ralph) — running Ralph autonomously
- **05.05-06** — backlog prep and integration

So the **dependency chain is clear**: you can't do AFK Ralph (05.04) without sandboxing. That's real.

But here's my concern: **you're conflating two things that should be separate in the learner's mind:**

1. **Why** sandboxing matters (the conceptual problem it solves)
2. **How** to set up Docker sandboxing (the implementation task)

Right now your description is mixing them, and that's making the scope fuzzy.

Let me ask you this directly:

**After this lesson, what should the learner be able to do?**

Option A: *Explain why Docker sandboxing is necessary for AFK Ralph to work safely* (conceptual takeaway)

Option B: *Set up Claude Code to run inside a Docker sandbox* (hands-on takeaway)

Option C: *Both, equally*

Because if it's C, I think you have **two lessons** here, not one. And I'd argue they should be:

- **05.03a**: "Why Ralph needs sandboxing" (the problem, the risk, the solution at a conceptual level)
- **05.03b**: "Setting up Docker sandboxes for Claude Code" (the how-to)

The first is ~5 minutes of watching you explain the constraint. The second is the "awkward" setup you mention.

**Which is it for this lesson? Or am I misreading what you want to teach?**

A: Nah I don't think so. I don't think there are two lessons here because it's obvious and they will have felt it to be obvious from the previous lesson. We're just really setting up something that they've already felt.

Q: Fair. They felt the friction in 05.02 — Ralph pinging for permissions constantly. **That's the problem statement already delivered.** So yeah, no need to spend a whole lesson re-explaining why sandboxing matters. They get it.

So this is really a **hands-on setup lesson**: *Set up Claude Code to run inside a Docker sandbox so that permission requests can be handled automatically in the next lesson.*

That's lean and it lands.

But now I need to probe the implementation side, because "a little bit awkward to do it" is a red flag for scope creep:

**What exactly are we teaching in this setup?**

Are we:
- [ ] Installing Docker (if they don't have it)?
- [ ] Understanding what a Docker sandbox *is* conceptually?
- [ ] Creating a Dockerfile for Claude Code?
- [ ] Running Claude Code inside the sandbox?
- [ ] Configuring permissions/environment variables inside the sandbox?
- [ ] Testing that it works?
- [ ] Building an audit log (your explainer mentions this)?

That last bullet worries me especially. Your explainer says:

> Build an audit log for instructor/admin actions:
> - Log all accountability actions
> - Display in UI for admins only

**Is that actually in scope here, or is that a leftover from a different lesson context?** Because "build an audit log with UI" sounds like a separate project entirely, not a setup step.

Help me understand: **What's the absolute minimum they need to do by the end of this lesson so that 05.04 can proceed?**

A: Yeah installing Docker Desktop, understanding what a Docker sandbox kind of is and what its constraints are, don't need to create a Docker file. We're just running Claude code inside the sandbox and testing it. Oh yeah let's not worry about building the audit log; that's not gonna be something we care about. We're not actually going to use this to build a feature.

Q: Perfect. That's **way** cleaner and I can feel the scope tightening.

So we're at:
1. Install Docker Desktop
2. Understand what a sandbox is + its constraints (why it matters for Ralph)
3. Run Claude Code inside the sandbox
4. Test that it works

That's a tight, purposeful lesson. **One takeaway: "I can run Claude Code in a Docker sandbox so Ralph can operate autonomously in the next lesson."**

Now let me ask about **prerequisites and assumptions**:

- Can I assume everyone has Docker Desktop available to install on their machine? (No weird corporate firewall situations we need to warn about?)
- Do they need to understand anything about Docker conceptually before we start, or are we teaching "what a sandbox is" from zero?
- When you say "run Claude Code inside the sandbox" — is this literally just opening Claude Code, pointing it at a project running in the sandbox, and letting it work? Or is there configuration/setup needed inside the sandbox itself?

And one more **sequence question**: 

Should we teach "what a Docker sandbox is + constraints" *before* they try to set it up, or *after* they've tried to run Claude Code once to feel the difference? I'm leaning toward before (build the conceptual model first, then the hands-on task), but I want to know if you've got a reason to flip that.

A: Yeah I think we can assume that everyone has Docker Desktop available. Surely there might be some corporate firewall situations but I'm not sure how we're going to solve it. I'm not sure that's something we need to solve for.

I don't think I want to sort of elide what a sandbox is really like. We could go into micro VMs and all that shit but I don't think it's very valuable for the user to actually understand deeply what a sandbox is. We just need to run it, yeah, run Claude code inside the sandbox. It's literally a command: `Docker sandbox run Claude`. Yeah let's teach what a Docker sandbox is before they try to set it up.

Q: Good. I like the pragmatism there — **we're not teaching Docker architecture, just "here's what this does and why it matters for Ralph."**

So the sequence is:
1. Conceptual: What a Docker sandbox is + its constraints (brief, not deep)
2. Hands-on: `docker sandbox run claude` and verify it works

That's clean.

One more thing before we lock scope: **What does "testing that it works" actually mean?**

Do they:
- [ ] Just verify Claude Code launches inside the sandbox?
- [ ] Run a quick Claude Code task inside the sandbox and see it complete?
- [ ] Verify that permission requests *would* be handled differently (can't run a full AFK test without 05.04's setup)?

I'm asking because this determines whether the lesson ends with "here's the command" or "here's the command, and here's what you'll notice is different when Ralph runs in 05.04."

Also — **after they run this, what state are they in?** Do they leave the sandbox running? Do they shut it down? Does it need to stay set up for 05.04, or does 05.04 start fresh?

That last bit matters for whether we include "how to keep it running" or "how to manage the lifecycle" in this lesson.

A: Yeah let's run an exploration task within the sandbox just to get it working.

Q: Perfect. **One more clarification on that exploration task:**

Should it be:
- [ ] A task they've already done before (re-running something from Day 1 to verify "it works the same in the sandbox")?
- [ ] A brand new, simple exploration task (so they see Claude Code working fresh in the sandbox)?

I'm asking because the choice affects the *narrative* of the lesson. If they re-run something familiar, the lesson says "sandboxing is transparent — your workflows just work." If it's new, the lesson says "here's a quick win to prove it's working."

I'd lean toward **re-running something familiar** (maybe from 01.02 or 01.03) because it reinforces that sandboxing is a *constraint layer*, not a *new way of working*. But I want to know your instinct.

And then — **final scope check before we write the summary**:

Does the sandbox stay configured and running after this lesson? Or do they tear it down? Because if it needs to stay active for 05.04, we should explicitly say "leave it running" at the end. If 05.04 assumes a fresh sandbox, we say "you can shut it down now — 05.04 will show you how to set it up again for AFK mode."

Which is it?

A: A brand new simple exploration task, I think. Exploration tasks are super cheap. It's basically just asking the LLM about the code base. The sandbox should stay configured and running after the lesson. They don't need to tear it down or do any maintenance. When you exit the process, it just stops the sandbox but it is then available and still set up for later use.

Q: Got it. **Clean and pragmatic** — they set it up, run a task to verify it works, leave it ready for 05.04.

Alright, I think we have enough to lock this down. Let me state back what I'm hearing and you tell me if this is right:

---

**Scope Summary**

**Lesson title**: Setting Up Claude Code in a Docker Sandbox

**Core takeaway**: I can run Claude Code inside a Docker sandbox so Ralph can operate autonomously in the next lesson.

**Prerequisites**: 
- Docker Desktop installed on their machine
- Familiarity with Claude Code workflow (from Days 1-2)
- Understanding that Ralph pings for permissions (from 05.02)

**In scope**:
- What a Docker sandbox is (brief, practical explanation — not deep architecture)
- Why sandboxing matters for Ralph's autonomous operation (connecting back to 05.02 friction)
- Running the `docker sandbox run claude` command
- Walking through a simple codebase exploration task inside the sandbox
- Verifying that Claude Code works as expected within the sandbox
- Understanding that the sandbox persists after exiting and is ready for 05.04

**Out of scope**:
- Deep Docker architecture or how sandboxes actually work under the hood
- Creating custom Dockerfiles
- Managing sandbox lifecycle (stopping, restarting, cleanup)
- Building audit logs or any feature development
- Troubleshooting corporate firewall issues
- Configuring environment variables or permissions inside the sandbox

**Teaching sequence**:
1. **Hook**: Remind them of the permission-request friction from 05.02 and why Ralph needs to run autonomously
2. **What is a Docker sandbox** — practical explanation of constraints (isolated filesystem, network, processes) without deep architecture
3. **Why this solves the Ralph problem** — permission requests can be handled automatically in an isolated environment
4. **Run the command** — show them `docker sandbox run claude` and walk through setup
5. **Run an exploration task** — pick a simple codebase, ask Claude Code to explore it, verify it works
6. **You're ready for 05.04** — sandbox stays running, ready for AFK Ralph setup

---

Does that land? Anything I'm misreading?
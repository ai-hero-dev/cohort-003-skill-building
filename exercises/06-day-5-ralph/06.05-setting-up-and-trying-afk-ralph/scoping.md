A: All right by this point in the previous exercise they will have run a setup docker sandbox, which means that they're able to run AFK Ralph. We're going to be running the feature that we're building. We're going to have started in the human in the loop section and we'll be building it now. This lesson is really all about just watching Claude code run and watching it work, and experiencing the hands-on feeling of using AFK Ralph for the first time

Q: I appreciate the clarity here, but I need to push back on the scope a bit — and I think your instinct is actually pointing at a real problem.

Let me map where we are:
- **05.02** (HITL Ralph): Learner runs Ralph in human-in-the-loop mode, makes decisions together with Claude
- **05.03** (Sandboxing): Learner sets up Docker sandbox — the *infrastructure* that enables AFK
- **05.04** (this lesson): "Watch Claude code run, experience AFK Ralph"
- **05.05** (Backlog prep): Prepare a backlog for Ralph
- **05.06** (Hook up backlog): Connect Ralph to the backlog

Here's my concern: **You're describing a lesson that's mostly passive observation.** "Just watching Claude code run" is not a learnable outcome. After this lesson, what can the learner *do* that they couldn't before?

I think there's actually a **scoping mismatch** here. What I'm hearing is three different things that need separation:

1. **"AFK Ralph setup + first run"** — Get AFK Ralph working with the same feature from 05.02, confirm it works autonomously. Learner gets hands-on confirmation that the sandbox is properly configured.

2. **"Watching and debugging AFK runs"** — Learn to *read* what AFK Ralph is doing, interpret the logs, spot when it's stuck or going wrong. This is a skill.

3. **"Understanding what AFK Ralph needs to succeed"** — The conditions (backlog format, agents.md setup, etc.) that make AFK Ralph actually effective at autonomous work.

Which of these is **actually** the core takeaway for 05.04? Because right now "watch it work" could collapse into any of them, and I suspect the real lesson is buried in there.

**What's the one thing the learner should walk away knowing how to *do* after this lesson?** Is it:
- "I can start an AFK Ralph run and verify it's working"?
- "I can read AFK Ralph's output and understand what it's doing"?
- "I know what AFK Ralph needs from me to work well"?

Let's get specific before we scope the content.

A: The core takeaway here is the feeling of power that you get when Ralph is running and doing the work. I can start an AFK Ralph run and use it to build a PRD basically. They'll have a PRD from a previous exercise and this will be essentially just building on that and completing the feature work.

Q: Okay, now we're getting somewhere real. But I need to challenge you on something important:

**"The feeling of power" is not a learning outcome.** Feelings are the *reward* for a well-designed learning experience, but they can't be the *objective*. The learner might feel amazing and still not know what to do next time.

Here's what I'm hearing underneath though, and I think this is the actual takeaway:

**"I can hand Ralph a PRD + an agents.md + a backlog, start it in AFK mode, and watch it autonomously execute feature work to completion."**

That's concrete. That's doable. The *feeling* of power comes because they've genuinely experienced autonomous execution.

But now I have some hard scoping questions:

1. **What's the actual task?** You mention "completing the feature work" — is this the *same feature* they built in 05.02 (HITL Ralph)? Or a *new feature*? 
   - If same feature: That's powerful because they see the difference between "me + Claude making decisions" vs "Claude going full-speed autonomous"
   - If new feature: They need to bring a PRD, which means they're managing two exercises at once (this lesson + prep work)

2. **How much of the "starting Ralph" and "managing the run" is in scope vs. already done in 05.03?**
   - 05.03 is "Setting up sandbox" (infrastructure)
   - 05.04 is... starting Ralph? Monitoring it? Both?
   - These could be separate lessons if the monitoring/interpreting piece is non-trivial

3. **What happens when Ralph gets stuck or fails?** Is debugging/troubleshooting *in scope* for this lesson, or is that "how to fix AFK runs when they break" — a lesson for later?

Let me be direct: **If this lesson is just "press start and watch," it's too thin.** The learner needs to do something, even if that something is "interpret what's happening" or "make a decision when Ralph asks."

What's the actual hands-on work the learner is doing while Ralph runs?

A: Yeah this is without the backlog though. This is just a PRD and a prompt. I think what we will be learning is we'll just be walking through the script that I have for running AFK Ralph. That's a little bit of extra knowledge there but it's not a huge script. It just essentially runs a coding agent in Docker Sandbox in a loop. The hands-on work they're doing is watching Ralph's output, seeing the code it's creating, and noticing that it's kind of similar to the Human in the Loop version. Essentially we've worked up to this stage in small steps and now this is the culmination of it.

Q: Okay, I see it now. This is a **capstone moment** — not a new skill lesson, but a "here's what all those pieces do together" lesson. That's valuable, but it changes how we scope it.

Let me push back on one thing though: **Walking through the script is not the core learning.** The script is just the *vehicle*. And honestly, if learners need to understand the script deeply to use Ralph, that's a problem — they should just be able to run it.

Here's what I think the real scope should be:

**IN SCOPE:**
- Starting an AFK Ralph run (the command, what it does)
- Reading Ralph's output and understanding the workflow (this is the actual learning)
- Seeing it complete feature work autonomously
- Comparing it mentally to the HITL version from 05.02 (same PRD, no human steering = different execution)

**OUT OF SCOPE:**
- Deep dive into the script internals (how the loop works, the implementation details)
- Debugging broken runs
- Backlog integration (that's 05.05-05.06)
- Building the PRD (that's from earlier exercises)

Here's my real concern though: **You said "watching Ralph's output and noticing it's similar to HITL."** But is that the right framing? 

The *interesting* insight isn't "it's the same" — it's probably something like:
- "It goes faster without human interruptions"
- "It makes different decisions because it's not being steered mid-run"
- "I can walk away and it keeps working"

**What should the learner *notice* when they watch the AFK run?** What's the teachable difference between this and HITL that they should leave understanding?

Because that determines whether we need to guide them through the output or just let them run it and discover.

A: Yeah I think that's true. I think what they are learning, though, is that the human of the loop version is a great way to learn how Ralph works and how best to steer it. The AFK is actually the end goal and where you want to get to.

Q: **That's a really important distinction, and it changes the lesson structure.**

So the teaching arc across these Ralph lessons is:
- **05.02 (HITL)**: Learn *how* Ralph works and *how to guide it*
- **05.04 (AFK)**: See the payoff — this is the real goal, autonomous execution
- **05.05-05.06**: Learn what Ralph needs from you (backlog structure, etc.) to actually work well at that goal

That's clean. I like it.

But here's where I need to push on scope: **If the core takeaway is "AFK is the end goal," then the lesson can't be passive.** The learner needs to leave understanding *why* AFK is better, not just experiencing the feeling.

So the hands-on work isn't just "watch the output" — it's **"compare this run to the HITL run and notice what's different."**

This requires:
1. They have the HITL run fresh in mind (or you replay key moments from it)
2. They run the same PRD through AFK
3. They actively notice: speed, decision quality, where it diverges, what it accomplished without steering

**Here's my scoping question:** Do they need to see the *entire* AFK run from start to finish? Or is this more about **"start the AFK run, let it work for a bit, then we'll come back to the results later in 05.05"**?

Because if it's a full run, that could be 30 minutes+ of watching. If this is meant to be a "hands-on" lesson (not passive), we might need to **scope it as "start the run and interpret the early output"** — then 05.05 becomes "see the completed results and prepare for the next phase."

What's the realistic runtime here, and does the learner need to see the *whole thing*?

A: I think we should just allow the users to play in this sandbox and just say, yeah, this exercise you are going to kick it off. It will stream stuff to you in the terminal so you watch what it's doing and kind of guide it from afar. Really we're learning to trust Ralph essentially and learning to believe that this is a way that we can code, which is essentially autonomously.

For me in the video that they'll watch, I'm just basically setting them up but a lot of this is gonna be done by them. They're not watching me do this; they're doing it themselves as a skills-based lesson.

Q: Perfect. Now we have real clarity. This is **a hands-on, skill-based lesson where the learner runs Ralph themselves and experiences autonomous execution firsthand.**

That's a much tighter scope than I was thinking. Let me reflect back what I'm hearing:

**Core takeaway**: "I can start an AFK Ralph run and watch it autonomously execute feature work — and I can trust it to work without my steering."

**The actual work the learner does**:
1. Start the AFK Ralph run (with the PRD from earlier)
2. Watch the terminal output stream in real-time
3. Experience the autonomy — no decisions to make, just observation
4. Let it run to completion (or at least far enough to feel the difference from HITL)

**What this lesson is NOT**:
- Deep dive into the script
- Debugging or troubleshooting broken runs
- Building backlog structure
- Understanding why it's better (that's the *feeling*, not the explicit teaching)

Here's my one remaining scope question: **How much guidance do they need while watching?**

Do you want to:
- **Option A**: "Here's how to start it, go" — minimal narration, they discover
- **Option B**: "Here's how to start it, and here's what you're watching for" — point out key moments in the output
- **Option C**: "Here's the setup, I'll narrate as it runs, you observe" — more like a guided experience

This matters because it changes lesson structure. Which feels right to you?

A: Option B.

Q: Excellent. Now we're getting the real structure.

So they start the run, and **you guide them to notice key moments in the output** — moments that show autonomous execution working. This is where the "trust" builds.

Before I nail down the final structure, I need one clarification:

**What are those key moments they should notice?**

For example, are you pointing out things like:
- "Watch — it's making a decision about file structure without asking you"
- "See how fast it's iterating? No waiting for human input"
- "Notice it's testing as it goes"
- "It hit a problem and recovered without you intervening"

And more importantly: **Do these moments connect back to what they learned in HITL?** Like, "In HITL you made that decision, now watch Ralph make it autonomously"?

Because if we're teaching them to *trust* Ralph, they need to see evidence that Ralph is making *good* decisions — not just *fast* ones. The key moments should prove that autonomy works.

What are the 3-4 most important things they should see in that output stream that will make them genuinely believe "this is a real way to code"?

A: I think they should see that the permissions setup is working and the Docker sandbox. They're not being asked whether they need to approve every bash command or approve every file write. They also can see that it's running tests and running type checks and it's running the feedback loops which we've talked about on day four. They can see that it's editing files and making changes and working exactly in the same way as it did in the human in the loop version, or making the same file edits as it would in the human in the loop version.

Q: Perfect. Now I have the teaching arc. Let me synthesize what you've said and propose the structure:

**The learner should notice:**
1. **Sandbox permissions working** — Ralph can execute commands freely (no approval gates)
2. **Autonomous feedback loops** — Tests, type checks running automatically (day 4 pays off here)
3. **File edits happening** — Same quality work as HITL, just without steering
4. **Continuity** — "This is the same Ralph I learned in 05.02, just running without me"

That's powerful because it ties **everything together**: the sandbox (05.03), the feedback loops (day 4), the agents.md steering (day 2) — all working *together* in autonomous mode.

One final scope boundary question before I write the summary:

**How much do they need to understand about what Ralph is *trying to accomplish*?**

In other words:
- Do they need to read the PRD before starting? (I assume yes)
- Do they need to understand the agents.md setup? (probably not deeply — that's been done)
- Do they need to *interpret* what Ralph is doing against the original PRD? (or is "it's working, trust it" enough?)

In other words: **Are they passively watching "stuff happening," or actively validating "Ralph is building what was asked"?**

This determines if they need prep work (read the PRD) or if they can just hit go.

A: They will have already read the PRD in the previous exercise. We'll be showing them the script that we pass into Ralph so they'll understand a bit of that. They're validating Ralph is building what was asked.

Q: Perfect. That's tight and purposeful. Now I have everything I need.

---

**Scope Summary**

**Lesson title**: Running AFK Ralph — Experience Autonomous Execution

**Core takeaway**: I can start an AFK Ralph run with a PRD and watch it autonomously execute feature work to completion, validating that it's building what was asked — without needing my steering.

**Prerequisites**: 
- Completed 05.02 (HITL Ralph) — understands how Ralph works and how to steer it
- Completed 05.03 (Sandboxing) — Docker sandbox is set up and working
- Completed day 4 (Feedback loops) — familiar with tests, type checks, TDD concepts
- Have a PRD from a previous exercise ready to build on

**In scope**:
- Show the script/prompt being passed to Ralph (what it's being asked to do)
- Start the AFK Ralph run
- Watch the terminal output stream in real-time
- **Guide learner to notice**:
  - Sandbox permissions working (commands execute without approval gates)
  - Autonomous feedback loops running (tests, type checks, without human intervention)
  - File edits happening and accumulating (same quality work as HITL)
  - Ralph completing the feature work against the original PRD
- Experience the contrast: "This is Ralph from HITL, now running without my steering"

**Out of scope**:
- Deep dive into the script internals or how the loop works
- Debugging broken AFK runs (later lesson)
- Backlog structure or integration (05.05-05.06)
- Building or understanding the PRD (previous exercise)
- Understanding *why* certain architectural decisions were made

**Teaching sequence**:
1. **Show the prompt/script** — Learner sees exactly what they're asking Ralph to do (context for validation later)
2. **Start the run** — Execute the command; output begins streaming
3. **Watch permissions in action** — First key moment: bash commands executing without approval (sandbox is working)
4. **Spot the feedback loops** — Tests and type checks running autonomously (day 4 concepts in action)
5. **See file changes accumulate** — Ralph editing, iterating, building (same as HITL, just faster)
6. **Validate against the PRD** — Step back: "Ralph built what we asked. No steering needed."
7. **Experience the shift** — Learner realizes: "This is the real goal. HITL was learning. AFK is production."

---

Does this capture it?
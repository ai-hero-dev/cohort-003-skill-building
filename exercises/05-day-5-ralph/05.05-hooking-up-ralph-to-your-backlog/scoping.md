A: Alright the theory here is that backlog Ralph is like a super awesome way to use Ralph because it allows you to parallelize your work. We're going to introduce that idea not necessarily through an explainer but through practical work. We're going to prefix the start of this lesson with that and basically say we are doing show don't tell here. This lesson is all about just setting up the repo to run with a backlog.

Q: Perfect. I'm reading this against the context of the full Day 5 arc:

- **05.01** - What is Ralph (theory)
- **05.02** - Trying HITL Ralph (hands-on, interactive)
- **05.03** - Sandboxing (infrastructure concern)
- **05.04** - Setting up and trying AFK Ralph (hands-on, autonomous)
- **05.05** - Hooking up Ralph to your backlog ← **we are here**
- **05.06** - Using the backlog to parallelize QA (the payoff)

I see what you're doing: lessons 1-4 are about *Ralph itself*. This lesson is about *integrating Ralph into a workflow*. And 05.06 will show the real power of that integration.

Before I nail scope, I need to push on what "setting up the repo to run with a backlog" actually means in practice. Let me ask directly:

**After this lesson, what specific action should the learner be able to execute?** Is it:

- A) "I can configure a backlog file in my repo and point Ralph at it"
- B) "I can create a backlog, configure Ralph to read it, and have Ralph start pulling tasks from it autonomously"
- C) "I can create a backlog, configure Ralph to read it, trigger a Ralph run, and observe it working through the backlog"
- D) Something else?

And a follow-up: **Does the learner actually run Ralph in this lesson, or is this purely configuration/setup that gets validated in 05.06?** That distinction matters hugely for scope — "show don't tell" could mean they see Ralph working, or it could mean they see the setup work in a way that makes the payoff obvious in the next lesson.

What's your intent here?

A: This is a purely configuration step that gets validated in 5.6.

Q: Got it. **This is a setup lesson that pays off later.** That's fine, but it means we need to be crystal clear about scope boundaries, because setup lessons are where scope creep dies.

Here's my read on what should be IN vs OUT:

**IN scope:**
- Creating/formatting a backlog file (what does Ralph expect?)
- Configuring Ralph to point at that backlog
- Verifying the configuration is correct (without running a full Ralph cycle)

**OUT of scope:**
- Why backlogs are powerful (that's the *payoff* in 05.06, not this lesson)
- How Ralph *uses* the backlog during execution
- Troubleshooting what happens when Ralph runs (that belongs in 05.06 when they actually run it)

But before I lock that down, I need to understand one thing about the "show don't tell" framing:

**You said "prefix the start of this lesson with that and basically say we are doing show don't tell here."**

What does "show don't tell" mean in the context of a *pure setup lesson*? Are you saying:

- A) The explainer shows the backlog format/config by example rather than describing it in prose?
- B) The lesson leads with a quick demo of what a backlog looks like before diving into setup?
- C) Something else?

Because if it's (A), I'm with you. If it's (B), that feels like it bleeds into 05.06's territory — you'd be showing the *payoff* before the lesson that validates it, which could undermine the structure.

What's your intention?

A: We're not going to be like 'all Ralph is doing is it's going to be using the GitHub CLI to grab GitHub issues.' GitHub issues is an easy thing for people to set up. I suppose if they don't have a GitHub log in, they should set up a GitHub log in and that kind of thing?

Q: Okay, so the backlog source is **GitHub issues** — that's concrete and lowers friction for learners. Good call.

But I'm hearing a new scope creep risk here. Let me pull this apart:

**What I think you're saying:**
- The backlog Ralph reads comes from GitHub issues
- Learners need a GitHub account and repo set up
- Ralph gets configured to pull from that repo's issues

**What I'm worried about:**
- Are we also teaching "how to create good GitHub issues" in this lesson?
- Are we teaching "how to set up a GitHub repo" in this lesson?
- Are we teaching "how to authenticate Ralph with the GitHub CLI" in this lesson?

Because those feel like three different things, and only one of them (the Ralph configuration piece) is actually about **hooking Ralph up to a backlog**.

Here's my question: **Can we assume the learner already has a GitHub account and a repo with some issues in it?** Or do we need to walk them through creating those from scratch?

If they *don't* have that setup, should that be a **prerequisite checklist** (quick "make sure you have X before starting this lesson") rather than something we teach *in* the lesson?

What's your expectation about what the learner brings to this lesson?

A: We're not teaching how to create good GitHub issues. We are sort of teaching how to set up a GitHub repo but I'm kind of assuming that as prerequisite knowledge. As long as the GitHub CLI has been authenticated (which we should teach in this lesson), then we can just give them a one-liner to set up a GitHub repo. I think we can assume the learner already has a GitHub account but we're going to be creating the repo during this lesson. The issues in it will be created in the next lesson.

Q: **Excellent.** That's crisp. Let me lock this down:

**Prerequisites:**
- Learner has a GitHub account
- Learner understands basic git/repo concepts (they've done 01-04 already, so this is safe)

**In scope:**
- Authenticate the GitHub CLI (if not already done)
- Create a GitHub repo via one-liner
- Configure Ralph to point at that repo's issues as a backlog source
- Verify the configuration is correct (show that Ralph can *see* the backlog structure, even though there are no issues yet)

**Out of scope:**
- Teaching GitHub concepts or workflows
- Creating issues (that's 05.06's job)
- Running Ralph or seeing it consume issues
- Teaching what makes a "good" issue

That feels **tight and purposeful**. The lesson ends with Ralph configured and ready, issues placeholder waiting for 05.06.

Now, **one more clarity question about the "show don't tell" framing:** 

You want to lead with "we're doing show don't tell" — meaning the learner is going to *do* the setup hands-on, not read about it. The lesson structure should be **procedural, not explanatory**. They authenticate, they create the repo, they configure Ralph, they verify. Step by step, doing the work.

Is that right? And if so, should the lesson *open* by showing what a configured Ralph backlog setup *looks like* (just visually, what files/configs exist), so they know what "done" looks like before they start building it?

A: Yup that looks good. I mean a configured Ralph backlog basically just means we're gonna be using the GitHub CLI to pull issues into. To be honest actually we don't even need to show that cause that's really connected this up to Ralph itself, which is really the subject of the next exercise. We're not actually running Ralph from within this lesson; we're just getting the repo ready to run Ralph on it.

Q: **Perfect.** Now I'm going to push back slightly, because I want to make sure the lesson has a satisfying endpoint.

If we're *not* showing what a "configured Ralph backlog" looks like, and we're *not* running Ralph, then the learner's validation that they did it right is... what exactly?

Right now the lesson is:
1. Authenticate GitHub CLI
2. Create a repo
3. Configure Ralph to point at it
4. ???

**Step 4 is the problem.** How does the learner know they configured Ralph correctly if they don't run it or see evidence that the configuration is valid?

I see three options:

**A) Add a verification step** — "Run this command to verify Ralph can read your backlog structure" (without actually *running* Ralph on tasks). This gives them confidence the setup worked.

**B) Show the configuration files/output** — After setup, show what the configured state looks like. "Here's what your Ralph config should point to. Here's what the GitHub CLI returns. You're done when you see X."

**C) Leave it as-is** — Trust that if they followed the steps, it's right. They'll find out in 05.06 when they run Ralph.

My take: **Option A is best.** A quick sanity-check command that proves "Ralph can see your repo and its issue structure" gives closure to this lesson without spoiling 05.06. It's not running Ralph; it's just proving the plumbing works.

What do you think?

A: Yeah add a verification step; makes sense. We could get them to, I guess, run human in the loop, Ralph, on it. Maybe in this lesson we hook it up to human in the loop, Ralph. We get them to create a dummy issue that then human in the loop, Ralph, can go and grab and close the issue to demonstrate that it works.

Q: Ohhh, I see what you're doing — **use HITL Ralph as the verification mechanism.** That's elegant because:

1. It proves the backlog integration works without spoiling the AFK Ralph magic
2. It leverages something they already know (05.02 was HITL Ralph)
3. It's a satisfying "it works!" moment

But I need to flag a scope concern here:

**You're now asking them to:**
- Authenticate GitHub CLI
- Create a repo
- Configure Ralph to read from it
- Create a dummy issue in that repo
- Run HITL Ralph on that issue
- Watch it complete the issue

That's actually a pretty full lesson. The original scope was "set up the repo to run with a backlog" — now you're adding "and prove it works by running HITL Ralph."

**Here's my question:** Is creating and managing that dummy issue part of the core "setup" work, or is it a validation detail?

Because if it's validation, I'd argue: **Keep it minimal.** One dummy issue, HITL Ralph closes it, done. Don't let the issue creation/management expand into teaching territory.

But I also want to make sure this doesn't step on 05.06's toes. In 05.06, they're "using the backlog to parallelize QA" — will there be fresh issues being created then, or will they be using the dummy issue from this lesson?

What's the relationship between the issue you create here and the issues they'll work with in 05.06?

A: I agree, yeah. It should be totally minimal. It's just a dummy issue, basically a hello world.

Q: **Perfect.** That's the right call. One dummy issue, HITL Ralph proves it works, move on.

Now let me confirm the teaching sequence before we finalize scope:

**My proposed order:**

1. **Authenticate GitHub CLI** — get that prerequisite out of the way first
2. **Create a GitHub repo** — one-liner setup
3. **Configure Ralph to read from that repo's issues** — the core integration work
4. **Create a dummy "hello world" issue** — minimal, just to have something in the backlog
5. **Run HITL Ralph on that issue** — verification that the whole chain works
6. **Clean up or note the issue closure** — wrap it up

Does that sequence feel right to you? 

And one last thing before I write the scope summary: **Should we explicitly tell them to delete the dummy issue after HITL Ralph closes it, or leave it there?** I ask because if issues stick around, 05.06 might have lingering test data. Small detail, but worth being intentional about.

A: Yep looks good. They don't need to delete the dummy issue. When it's closed it will no longer show up in future runs.

Q: **Perfect.** Closed issues won't clutter future runs. Clean.

Alright, I have everything I need. Here's the **Scope Summary**:

---

**Scope Summary**

**Lesson title**: Hooking Up Ralph To Your Backlog

**Core takeaway**: You can configure Ralph to pull tasks from GitHub issues and verify the integration works by running HITL Ralph on a test issue.

**Prerequisites**: 
- Learner has completed 05.02 (HITL Ralph fundamentals)
- Learner has completed 05.04 (AFK Ralph setup)
- Learner has a GitHub account
- Learner understands basic git/repo concepts

**In scope**:
- Authenticating the GitHub CLI (if not already done)
- Creating a GitHub repo via one-liner
- Configuring Ralph to read from that repo's issues as a backlog source
- Creating a minimal "hello world" dummy issue
- Running HITL Ralph on that issue to verify the integration works
- Observing Ralph close the issue, proving the backlog chain is functional

**Out of scope**:
- Teaching GitHub workflows or best practices
- Creating substantive issues (that's 05.06's job — this is a throwaway test issue)
- Running AFK Ralph (that's 05.06's payoff)
- Teaching how Ralph *uses* the backlog during execution
- Explaining *why* backlogs enable parallelization (that's 05.06's framing)

**Teaching sequence**:
1. **Authenticate GitHub CLI** — prerequisite plumbing; gets it out of the way so everything downstream works
2. **Create a GitHub repo** — gives learners a concrete target to hook Ralph into
3. **Configure Ralph to point at that repo's issues** — the core integration work; learner now has Ralph aware of a backlog source
4. **Create a dummy "hello world" issue** — provides something for Ralph to act on; minimal scope, just a test case
5. **Run HITL Ralph on that issue** — verification step; proves the entire chain (repo → backlog → Ralph) works; gives closure to the lesson
6. **Observe issue closure** — wrap-up; confirms success without over-explaining

---

This lesson is **pure setup with minimal validation**. It ends with learners ready to run Ralph autonomously in 05.06, but it doesn't spoil that lesson's real payoff (parallelization). Good structure.

Ready to write?
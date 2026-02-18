A: So I want to: this exercise is basically a very simple explainer on setting up context usage in the Claude Code status line. The idea here is that we want users for the rest of the workshop to be carefully monitoring the context window and Claude Code doesn't provide that by default so we need to figure that out now. I provided you with an article on how to do it and while the article does show quite a lot of fancy stuff in there, the only thing that we really care about is the context usage, the percentage on the end. What we want to do is create a slimmed down version of this tutorial that just covers that context usage bit.

Q: Perfect! I love that angle—keeping it lean and focused. So basically we're stripping away all the git status stuff and the fancy repo naming, and just honing in on **"how do I get that context percentage showing in my status line?"** because that's the real blocker for the rest of the workshop.

A couple of quick questions to make sure I nail this:

1. **Setup complexity**: Do you want to keep it super minimal (like, "install ccstatusline, add this config, done") or do you want to walk through the wrapper script setup too? Or should we test what the bare minimum actually is?

2. **Target audience**: Are we assuming people are already comfortable with Claude Code and just need the quick wins, or should we assume some folks might be setting it up for the first time?

3. **Tone**: Should this feel like "here's the quick 5-minute fix" or more of a "here's what's happening under the hood so you understand it"?

My thought is we could structure it as:
- **Why this matters** (context paranoia 😄 - keep it brief)
- **The absolute simplest path** to get that percentage showing
- **One quick screenshot/demo** of what it looks like
- Done.

Does that feel right to you, or would you want to adjust anything?

A: Yeah the target audience here, they've already seen, they've already had a go at building a feature with Claude code. They obviously know what Claude code is and why context window is important. This is really just a step list of steps to complete in order to set this up. The context paranoia is really important because we need it to be super visible. Having it right there as your coding, seeing it go up, is something I naturally reach to whenever I'm working with Claude code and I find it an essential piece of feedback.

Q: Got it—so this is pure practical setup. They already get *why*, they just need the *how*.

So we're looking at:
- **Brief intro** on why this matters (the "constant source of paranoia" angle—that constant visibility is key)
- **Step-by-step instructions** to get that percentage showing
- **Stripped down** from the article (no git stuff, no repo naming, just the context percentage)
- **Clean and scannable** so they can power through it

One thing I want to confirm: in your article, you've got both `ccstatusline` config AND the wrapper script. For the slimmed version, do you want to go with the absolute simplest path (just install ccstatusline + minimal config), or do you think the wrapper approach is worth keeping since it's still pretty straightforward?

Also—should we keep it command-line focused, or would a quick visual help (like "here's what it looks like when it's running")?

My sense is we go: install → configure → done. No fluff, just get that number in their face.

Sound good?

A: Let's go live! Start the interview based on what we discussed.

Q: Perfect! Let me start fresh with you then.

---

Hi! I'm here to help you create a streamlined version of this tutorial. I've reviewed your original article, and I can see you've got a lot of great detail in there about the full status line setup. But as you've said, we're focusing this down to just the context percentage piece—because that's the real blocker for your workshop participants.

So let's dig in:

**First question: In your original article, you mention this context percentage is "a constant source of paranoia" for you. Can you paint a picture of what that actually feels like when you're coding with Claude Code? Like, what's the anxiety you're trying to solve for people?**

A: Oh no you absolutely want that healthy paranoia about context window because as soon as you slip over the 40% threshold you're gonna end up in the dumb zone, which we've talked about already in the course. Surfacing a Claude code usage is something that it doesn't do by default and I really wish it did. That's what I'm trying to fix for you here.

Q: Ah, so **40% is the magic threshold**—once you cross that, the AI starts degrading noticeably. That's super concrete and actionable.

So here's what I'm curious about: **When you're in the middle of coding and you hit that 40% mark, what do you actually *do* about it?** Do you stop mid-feature? Start a fresh session? Clear context somehow? I want to understand the workflow impact so we can make sure people understand why they need to be watching this number *while* they're working, not just noticing it after the fact.

A: Don't worry about that. That's out of scope.

Q: Fair enough! Let's stay focused.

So when someone installs this and gets that percentage showing in their status line, **how often do you think they should be glancing at it?** Like, is this something they check constantly throughout a coding session, or more of a periodic sanity check?

A: Yeah literally whenever you're making a decision about whether to continue the context or not, it should be along with seeing the actual output. It should be the second thing that you glance at.

Q: Got it—so it's always *there*, right in their line of sight, so when they're deciding "should I keep going or do something about this?" they've got that number front and center. No hunting for it.

**Quick practical question: In your original article, you've got the `ccstatusline` tool as the core piece that actually gives you that percentage. Have you tested whether there's a simpler way to get that number, or is `ccstatusline` genuinely the best/only solid option out there?**

A: I haven't seen a way to do this without ccstatusline.

Q: Perfect. So `ccstatusline` is the tool we're built around.

Now, looking at your original article, you've got quite a few moving pieces—the config file, the command script, the wrapper script. **For someone who just wants that percentage showing and nothing else, what's actually the bare minimum they need to install and configure?** Can we strip it down further, or is all that scaffolding necessary?
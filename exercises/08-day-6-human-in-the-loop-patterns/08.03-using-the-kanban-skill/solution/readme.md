Time to rock and roll. The task is to review a GitHub issue, and the AI agent is heading off to explore the repo to understand what needs to be done.

It quickly returns with a potential list of issues. When checking these, it's always good to verify the first one is a proper tracer bullet and not some horizontal splurge.

### Understanding the Tracer Bullet

The first issue looks really good because it covers XP on lesson completion plus sidebar level display. This involves:

- Doing the XP events table and migration
- Writing tests for the XP service
- Showing the UI

![Claude Code showing a the first tracer bullet issue](https://res.cloudinary.com/total-typescript/image/upload/v1773385941/ai-hero-images/hebcx4cqd8yodjkksrqw.png)

That's exactly what you want. The remaining issues extend from this:

- **Streak tracking** - an extension of the original tracer bullet
- **Quiz XP** - another extension
- **Issues #4 and #5** - look like really small pieces, so they get merged together
- **Issue #6** - the full gamification verification (proper QA plan)

## Merging Small Tasks

Issues #4 and #5 look too small on their own, so merge them together. Submit this, and it should plunk those two together into a single, more substantial task.

![Claude Code showing the request to merge issues 4 and 5 together](https://res.cloudinary.com/total-typescript/image/upload/v1773385942/ai-hero-images/gkhboqll3ejypp4uavzk.png)

The AI agent is now asking for permission to create these as GitHub issues. They look good, and since they're derived from the conversation anyway, you can see them all on the issues template once they're done.

## Configuring Permissions

The agent is asking for permission for each individual issue. Rather than approving each one manually, it's time to go into your settings configuration.

There's a `settings.json` file (or `settings.local.json`), and you want to add bash support for the `gh-issue-create` command. This allows the agent to create issues without asking for permission each time.

```json
{
  "permissions": {
    "allow": ["Bash(gh issue create *)"]
  }
}
```

This should hopefully speed things up.

You're using GitHub here, but you could definitely use any kind of task tracker that has a CLI or has an MCP server. The principle is the same - automate the issue creation so the AI can work faster.

## Viewing the Created Issues

The agent has created all five issues. In the UI, you can see them all listed: issues #57 (the PRD), and #58, #59, #60, #61, #62.

![GitHub showing the created issues in a list](https://res.cloudinary.com/total-typescript/image/upload/v1773385943/ai-hero-images/emkscejzg9yh9fzn3dbq.png)

Let's take a look at one of them as an example. This is issue #61, the one that was grouped together - the dashboard summary card and the module completion toast. It's really thin, just a couple of lines describing what needs to be built as part of this plan. It tells you to go and see the original PRD for full details, and then lists a bunch of acceptance criteria.

Now let's look at the QA one, which is the last one here (issue #62). It's basically got a big list of checkboxes for all the work that was completed.

![A GitHub issue showing the QA checklist with multiple checkboxes](https://res.cloudinary.com/total-typescript/image/upload/v1773385944/ai-hero-images/uugx2kjamfqti36nebgb.png)

Adding the QA plan and showing it to the LLM is valuable because it shows the agent what the user is going to do at the end. It provides another source of constraints - these acceptance criteria must be met, this is what the user will verify.

## Setting Up the AFK Loop

Now you're all set up and ready to run the AFK loop. You're going to run it with 10 max iterations. Recently, the default has shifted to running it with 100 iterations as the default. It sounds slightly mad, but honestly, there haven't been any issues with it yet.

This time, you're going to go full AFK (Away From Keyboard) for this one. You'll come back once it's done its iterations - unless you hit any weird issues on the way, which hopefully won't happen.

```bash
./ralph/afk.sh 10
```

## Results After the AFK Loop

After some time has passed, there are only two open issues remaining:

- The original PRD (issue #57)
- The human-in-the-loop QA task (issue #62)

The agent completed the work after four iterations and you're now up to nearly 400 tests. It completed each issue in order, which is exactly what you want.

![GitHub issues showing only the PRD and QA task remaining open](https://res.cloudinary.com/total-typescript/image/upload/v1773385944/ai-hero-images/tkdtxslls6gegmd1fsqq.png)

## Walking Through the QA Plan

Now it's time to walk through the QA plan and verify that everything works.

First, log in as a student and go to the dashboard. There's an early fix needed - the migration hasn't run, so run it locally:

```bash
pnpm db:migrate
```

Now you should be able to refresh the page and everything loads correctly. You can see lots of UI has been added here.

![The dashboard showing the newly implemented gamification UI](https://res.cloudinary.com/total-typescript/image/upload/v1773385945/ai-hero-images/emrxgbhydltuwl6nmrgn.png)

### Checking the Implementation

During the QA process, start looking at things you don't like. For instance, the stars and flames displaying in light mode might look different than the ones on the sidebar. The padding at the top of the board might seem weird. These observations go into GitHub issues.

Let's continue with QA. Go into a course, click continue learning, and complete a lesson by pressing "up next". You should get 10 XP - yes, that works beautifully.

![Completing a lesson and receiving 10 XP](https://res.cloudinary.com/total-typescript/image/upload/v1773385946/ai-hero-images/pn0lpq3cazpfo3hhdl3e.png)

Check off that test, then complete the same lesson again to verify no duplicate XP. Go back to the pagination and filtering lesson, press "up next" again, and you don't get duplicate XP. Good.

Now find a quiz to pass for the first time and verify that 5 XP is awarded. To do that, log in as a different student and find one on the API Fundamentals HTTP Methods quiz. After answering the questions and submitting, you get 5 XP. Beautiful.

![A quiz being completed with 5 XP being awarded on submission](https://res.cloudinary.com/total-typescript/image/upload/v1773385946/ai-hero-images/sthe1cphtxc5afdhix7o.png)

There's nothing duller in the world than watching someone just follow a QA script. So do as much as you feel comfortable with - once you've got the picture, finish up to save your sanity. This is a toy project after all.

## The Value of AFK and Human-in-the-Loop Tasks

The important thing about the Kanban skill, and what's really valuable about this process, is that AFK (automated for known patterns) and human-in-the-loop tasks are first class citizens.

You can plan huge tranches of work while not quite knowing how all your tasks are going to be applied yet. You could even modify this skill to break the QA stages up into sections, so you're only QAing certain bits instead of large chunks.

And of course, you can delegate this to different members of your team if you have a testing specialist.

### Building Humans Into Your Dev Loop

The AFK versus human-in-the-loop designation allows you to build humans into your dev loop in a really intuitive way. You're not trying to eliminate humans - you're augmenting the development process.

This exercise shows you how to do exactly that. Nice work, and I'll see you in the next one.

## Summary of What Was Built

| Feature                 | Status                     | Tests                   |
| ----------------------- | -------------------------- | ----------------------- |
| XP on Lesson Completion | Complete                   | 18 new tests            |
| Sidebar Level Display   | Complete                   | Included in UI tests    |
| Streak Tracking         | Complete                   | 18 new tests            |
| Quiz XP (First Attempt) | Complete                   | 6 new tests             |
| Dashboard Summary Card  | Complete                   | 6 new tests             |
| Module Completion Toast | Complete                   | Included in toast tests |
| **Total**               | **All AFK tasks complete** | **~390 tests passing**  |

The QA plan (`issue #62`) remains open for human verification, allowing you to catch edge cases and polish the user experience before merging.

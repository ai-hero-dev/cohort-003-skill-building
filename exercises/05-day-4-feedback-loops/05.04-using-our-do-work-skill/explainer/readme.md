# Using Our `/do-work` Skill

We've built a `/do-work` skill that guides agents through structured feedback loops. Now it's time to test it on a realistic feature - the in-app notifications PRD.

The PRD describes a problem: instructors on the Cadence platform can't tell when new students enroll. They have to manually check their student list or analytics dashboard. This creates a gap where they miss the chance to engage with new students promptly.

This is a perfect test case because it's substantial enough to be meaningful, but contained enough to fit within a single phase. As the agent works through it, watch carefully to see if it's actually following the `/do-work` skill steps and running the feedback loops you designed.

## Steps To Complete

### Setting Up Your Test

- [ ] Open a fresh Claude Code session

Start with a clean slate so you can observe the agent's behavior without any prior context.

- [ ] Invoke the `/do-work` skill with the plans and PRD

Pass in both the in-app notifications plan and PRD files:

```
/do-work @plans/in-app-notifications.md @prd/in-app-notifications.md do phase one
```

### Observing the Agent's Behavior

- [ ] Watch whether the agent follows your `/do-work` skill steps

As the agent works, check:

- Does it follow the steps you laid out in the skill?
- Is it actually running the feedback loops you designed?
- Does it pause to get feedback before moving forward?
- Does it incorporate that feedback into its work?

- [ ] Take detailed notes on what you observe

Write down:

- Which steps did the agent execute correctly?
- Which steps did it skip or handle poorly?
- Did the feedback loops trigger as expected?
- Where did the agent deviate from your skill?

### QA'ing the Output

- [ ] Review the code the agent generated

Check that it actually implements the in-app notifications feature described in the PRD.

- [ ] Test the implementation manually

Run the code locally and verify that:

- Notifications appear when new students enroll
- The notifications are visible to instructors
- The feature works as described in the PRD

- [ ] Note any bugs or incomplete work

If the agent missed something or the code doesn't work, document what needs to be fixed.

### Getting Help

- [ ] Share observations in Discord if you hit any issues

If something isn't working the way you expected, post in Discord with specifics about what went wrong. This will help us all improve our skills.
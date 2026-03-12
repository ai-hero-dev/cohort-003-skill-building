# Using the Kanban Skill

You've now seen what the Kanban skill looks like in action. It's time to put it into practice with a real PRD and watch how it transforms user stories into actionable issues.

We're building a gamification system. Players want XP when they complete lessons, they want levels to grind toward, and they want streaks to maintain. These features won't make the platform any better, but they'll make it feel more rewarding.

Your job is to take a PRD, convert it into issues, and let an AI agent handle the implementation work.

## Steps To Complete

### Set Up Your PRD

- [ ] Copy the PRD from the [GitHub gist](https://gist.github.com/mattpocock/43640c8d45c7a0e4c1166a3b3665ce05)

Paste it into a new GitHub issue in your repository, just like the example shown with issue #57.

- [ ] Note the issue number

In the example, the PRD was issue #57. Write down whatever issue number you get.


### Convert the PRD to Issues

- [ ] Open Claude Code and run the `PRD to issues` command

Pass in your PRD issue number. For example:

```
PRD to issues
57
```

This will create individual issues for each user story in your PRD. Let it complete fully before moving on.

- [ ] Observe what the Kanban skill does

Write down your observations about the approach. Do you like how it breaks down the PRD? Are the issues well-structured? Is anything missing?


### Run Ralph on the Generated Issues

- [ ] Execute the Ralph loop on your newly created issues

Run the AFK (Away From Keyboard) task runner and let it pick up the automation-friendly issues. This should only grab tasks that don't require human judgment.

```
./ralph/afk.sh 10
```

This runs up to 10 automated tasks. The agent will select issues with no blockers and implement them end-to-end.

- [ ] Observe the implementation process

Watch as the agent works through multiple issues. It will create schema changes, write tests, integrate code, and commit everything automatically.

- [ ] Check what remains

After Ralph finishes, you should be left with human-in-the-loop QA tasks that need manual review. These are the issues marked as HITL that require human judgment.


### Review the Results

- [ ] Examine the generated code and tests

Look at the commits created by Ralph. Do the implementations match the user stories? Are the tests comprehensive?

- [ ] Review the remaining HITL issues

These are tasks that need human sign-off. Read through them and understand what manual work still needs to happen.

- [ ] Note any patterns you observe

What kinds of tasks did Ralph handle well? What required human input? How did the Kanban skill's issue breakdown help or hinder the agent's work?
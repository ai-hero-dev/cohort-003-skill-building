You've now seen what the Kanban skill looks like in action. Time to use it yourself with a real product requirements document (PRD).

The PRD we're using focuses on gamification features. Every course platform needs them, right? XP, levels, streaks - the useless doodads that make learning feel rewarding.

Your task is to convert this PRD into actionable GitHub issues, then run an AFK loop to implement the automated tasks. You'll see firsthand how the Kanban board approach works for managing AI-assisted development.

## Steps To Complete

### Setting Up the PRD and Issues

- [ ] Copy the PRD from the [GitHub gist](https://gist.github.com/mattpocock/43640c8d45c7a0e4c1166a3b3665ce05)

Paste the entire content into a new GitHub issue in your repository.

- [ ] Note down the issue number

This becomes your PRD reference. In the video example, it's issue #57.

- [ ] Create a new Claude Code chat and use the `/kanban` skill

Pass in your PRD issue number:

```
/prd-to-issues #57
```

Let the command finish running and observe the output carefully.

### Running Your AFK Loop

- [ ] Review the issues that were created

Write down what you notice about the approach. Do you like how the issues were structured? Are the user stories clear?

- [ ] Run a Ralph loop on the resulting issues

The command should look something like this:

```
./ralph/afk.sh 10
```

The `10` tells Ralph to work for up to 10 iterations. Ralph will automatically pick up tasks marked as AFK (automated for known patterns).

- [ ] Let Ralph run to completion

Once Ralph finishes, you'll have implemented features, run tests, and committed code. The remaining work will be human-in-the-loop QA tasks - code that needs human review before it's merged.

- [ ] Review what Ralph accomplished

Check the git log to see the commits. Look at the test results. Notice which issues are now closed vs which ones are still open for human review.

That's it! You've now used the Kanban skill in a real workflow.

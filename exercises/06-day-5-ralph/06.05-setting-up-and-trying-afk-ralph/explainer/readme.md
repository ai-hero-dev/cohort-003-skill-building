# Running AFK Ralph - Experience Autonomous Execution

You've learned how Ralph works in human-in-the-loop mode. You've set up the Docker sandbox that makes autonomous execution possible. Now it's time to experience the real goal: watching Ralph run completely independently.

This is where all the pieces come together. The same PRD, the same agents setup, the same feedback loops from day 4, but now Ralph executes without needing your decisions. You're going to start the run, watch the terminal stream in real-time, and see autonomous development actually happen.

The key moments you'll notice: commands executing without approval gates, tests and type checks running automatically, files changing and accumulating. This is Ralph doing what you asked, at full speed, without steering.

## Steps To Complete

### Prepare and Review

- [ ] Have your plan and PRD ready

You'll be passing both to Ralph, just like in HITL mode, but without the human steering.

- [ ] Review the script you'll be running

Look at the `./ralph/afk.sh` script in your exercise folder. You don't need to understand every detail, but note that it takes your plan, PRD, and a maximum number of iterations as arguments.


### Start Your AFK Run

- [ ] Run the AFK Ralph command with your plan, PRD, and max iterations set to 1

```bash
./ralph/afk.sh "plans/admin-analytics-plan.md prd/admin-analytics.md" 1
```

Output will stream to your terminal as Ralph works. The max iterations limit prevents Ralph from looping forever.

- [ ] Watch for these key moments as Ralph runs:

**Sandbox permissions working**: You'll see bash commands executing without any approval prompt. Ralph can run code, write files, execute tests, all autonomously.

**Feedback loops in action**: Tests and type checks run automatically as Ralph works. These are the day 4 concepts you learned, now running without human intervention.

**File changes accumulating**: Watch as Ralph edits files, iterates, and builds. The same quality work you saw in HITL, just faster and uninterrupted.

- [ ] Let the run complete

When Ralph finishes or reaches the iteration limit, the terminal will show the completion message.


### Validate What Ralph Built

- [ ] Compare the output against your original PRD

Did Ralph build what you asked for? Look at the files it created, the changes it made, the tests it wrote. Is this aligned with your PRD?

- [ ] Notice what's different from HITL mode

In HITL, you made decisions mid-run. Ralph asked you questions. Here, none of that happened. Ralph made autonomous choices and kept moving.

- [ ] Write down 3-5 observations

What surprised you? What worked well? What would you want to steer differently next time?


### Document Your Experience

- [ ] Note any moments where Ralph did something unexpected

Did it make a choice you wouldn't have made? Did it recover from an error? Did the feedback loops catch something?

- [ ] Identify what Ralph needed to succeed

Was the PRD clear enough? Did the agents setup help? Did the sandbox permissions allow what needed to happen?

- [ ] If you hit any issues, head to the Discord

Setup problems? Ralph getting stuck? Share what you're seeing and we'll help debug.
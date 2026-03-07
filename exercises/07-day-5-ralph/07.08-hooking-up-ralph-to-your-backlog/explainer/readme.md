# Hooking Up Ralph to Your Backlog

Ralph is a powerful autonomous coding agent, but it needs a clear queue of work to process. Right now, Ralph works through tasks manually. What if we could automatically feed Ralph tasks from a backlog that it processes one by one, completely unattended?

That's where GitHub issues come in. Your repository's issues become Ralph's task queue. Ralph can read them, work on them, and update them as it goes - creating a continuous feedback loop between your planning and Ralph's execution.

In this lesson, we're going to connect Ralph to your GitHub issues so it can work through your backlog autonomously.

## Steps To Complete

### Set Up Your GitHub Issues

- [ ] Create a new GitHub issue for your Admin Analytics PRD

Copy the entire PRD file and paste it into a new issue titled "admin analytics PRD". This becomes issue #1 in your repository.

- [ ] Create a second GitHub issue for your Admin Analytics Plan

Copy your plan file and paste it into a new issue titled "Admin Analytics Plan". In the issue body, reference the PRD issue using `#1` instead of a local file path. This becomes issue #2.

These GitHub issues now serve as your task backlog. Ralph will read them, understand what needs to be done, and work through them systematically.

### Authenticate Docker Sandbox with GitHub

Before Ralph can access your GitHub issues, you need to give your Docker sandbox permission to talk to GitHub via the GitHub CLI.

- [ ] Start a new Docker sandbox and authenticate with GitHub

```bash
docker sandbox run claude .
```

Once the sandbox starts, press the `!` key to enter bash mode, then run:

```bash
gh auth login
```

Complete the OAuth flow by copying the device code and visiting `github.com/login/device` in your browser. Once complete, you can press `CTRL-C` to exit.

Your Docker sandbox is now authenticated and can access your GitHub issues.

### Update Ralph's Prompt with Task Prioritization

Ralph needs to understand which tasks matter most. The prompt file should explain your priority order for different types of work.

- [ ] Open `ralph/prompt.md` and review the task selection section

This section defines how Ralph chooses which issue to work on next. The priority order shown is:

1. **Critical bugfixes** - These are highest priority because bugs can block other work
2. **Development infrastructure** - Tests, types, and dev scripts need to be solid before building features
3. **Tracer bullets for new features** - Small end-to-end slices that validate your approach
4. **Polish and quick wins** - Small improvements and additions
5. **Refactors** - Code cleanup and improvements

This priority order makes your backlog versatile. It can contain PRDs, plans, bug reports, infrastructure tasks, and refactoring requests all mixed together - and Ralph will work through them in a sensible order.

### Update Your AFK Script to Include GitHub Issues

Ralph's script needs to fetch your open GitHub issues and pass them to Claude as context.

- [ ] Open your `ralph/afk` file

Look for where the script collects context about your repository. It currently gathers recent commits. You need to add a line that fetches your open issues using the GitHub CLI:

```bash
issues=$(gh issue list --state open --json number,title,body,comments)
```

This command uses the GitHub CLI to list all open issues with their full details including comments. Add this line alongside where commits are being gathered.

- [ ] Update the prompt variable to include the issues

The `prompt` variable in your script should pass three pieces of context to Claude: previous commits, your GitHub issues, and your prompt file. Make sure all three are being passed to the Claude command.

### Run Ralph in AFK Mode

Now Ralph is ready to work through your backlog autonomously.

- [ ] Run your Ralph script with max iterations set to 5

```bash
./ralph/afk 5
```

Ralph will start processing issues from your backlog. It will:

1. Read your open issues
2. Pick the highest-priority task based on your priority order
3. Explore your codebase
4. Implement the task
5. Run your feedback loops (`pnpm run test`, `pnpm run typecheck`)
6. Make a git commit with details about what it did
7. Either close the issue (if complete) or comment on it (if incomplete)

When Ralph runs out of tasks, it will return `<promise>NO MORE TASKS</promise>` and exit with "Ralph complete after X iterations."

- [ ] Observe what Ralph accomplishes

Watch the terminal output to see Ralph work through your issues. Pay attention to:

- Which issue it chose first (should match your priority order)
- How it breaks down the task
- Whether tests and typecheck pass
- The commit messages it creates
- Whether it closes issues or leaves comments

### Test Ralph's Work and Create a New Issue

Now that Ralph has completed the backlog, it's time to QA the results.

- [ ] Navigate to your application and test what Ralph built

Explore the features that were implemented. Make sure they work as expected and integrate well with the rest of your codebase.

- [ ] Find something you'd like to improve or change

As you explore, look for small tweaks or polish that could be better. This might be a default value that should change, a UI element you'd like adjusted, or a minor feature enhancement.

- [ ] Create a new GitHub issue describing the improvement

Write a clear, concise issue describing what you want changed and why. For example: "The analytics page for admins should default to 12 months instead of 30 days, since admins need to view longer time periods."

- [ ] Run Ralph again to work on your new issue

```bash
./ralph/afk 5
```

Ralph will see your new issue, pick it as the next task (assuming it matches your priority order), and work on it autonomously. This time you'll see Ralph tackle a different type of task without any intervention from you.

- [ ] Verify the change was made correctly

Test your application again to confirm Ralph implemented the improvement. If everything looks good, you've successfully demonstrated Ralph's continuous feedback loop: plan → execute → QA → plan again.

This cycle is what makes Ralph valuable. Once your backlog is set up, you can continuously feed it new tasks and watch them get completed automatically.
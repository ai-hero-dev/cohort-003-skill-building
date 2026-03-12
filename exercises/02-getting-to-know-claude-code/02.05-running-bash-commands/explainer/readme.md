Claude Code becomes much more powerful when you can execute bash commands and give it feedback. Instead of just writing code, Claude can run tests, check files, and respond to real output from your project.

There are three ergonomic ways to interact with bash while Claude Code is running. Each one serves a different purpose, and knowing when to use each will make your workflow much smoother.

![Diagram 1](https://res.cloudinary.com/total-typescript/image/upload/v1773081196/ai-hero-images/c9xiefsbqh2udyxl6y6q.png)

## Steps To Complete

### Running Quick Commands

- [ ] Start a bash command with the `!` prefix

Type `!` followed by your command. For example:

```bash
! npm run typecheck
```

Claude executes the command immediately. The output appears in the terminal and is automatically incorporated into Claude's context.

- [ ] Let Claude see and respond to the output

If there are errors, Claude can analyze them and suggest fixes. This is perfect for quick checks: running tests, checking file contents, or verifying your setup.

### Starting Long-Running Processes

- [ ] Run a long-running command like a dev server

Type the command without any prefix:

```bash
npm run dev
```

The process starts and begins outputting to the terminal.

- [ ] Press `Ctrl+B` to background the process

While the command is running, press `Ctrl+B`. The process moves to the background and a status message appears.

- [ ] Navigate to the background task indicator

Press the down arrow key to move to the background task display at the bottom of the screen.

- [ ] View the background process logs

Press return to open the background task. You can now see what's happening with the dev server, including the localhost URL it's running on.

- [ ] Return to Claude Code

Press the left arrow to go back to the main Claude Code interface. The process keeps running in the background.

Claude can see where the logs are being written and can interact with your project, making requests to the dev server or checking its output while debugging issues.

### Taking Full Terminal Control

- [ ] Press `Ctrl+Z` to suspend Claude Code

Claude Code pauses completely. The terminal is now yours to control.

- [ ] Run any commands you want

These commands are hidden from Claude:

```bash
echo foo
```

Claude won't see or act on anything you run while suspended.

- [ ] Type `fg` to resume Claude Code

```bash
fg
```

Claude resumes exactly where it left off with all its previous state intact. Any commands you ran during suspension aren't visible to Claude, but the session continues seamlessly.

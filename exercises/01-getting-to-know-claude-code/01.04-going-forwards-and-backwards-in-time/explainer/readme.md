# Going Forwards And Backwards In Time

## Introduction

Claude Code lets you navigate your conversation history like you're moving through time. Made a change you want to undo? Just ask Claude to revert it. Need to go back further? You can rewind your entire session to any previous point.

This is incredibly useful when experimenting. You can try something out, see if it works, and if it doesn't, step back to where you were without losing your conversation history.

Claude also persists all your sessions locally. That means if your session gets interrupted, you can always resume exactly where you left off.

## Steps To Complete

### Understanding Rewind Mode

- [ ] Open Claude Code and make a change to your codebase

Ask Claude to do something simple - add a new file, modify existing code, or remove something.

- [ ] Ask Claude to revert the change

Say something like "revert that, please" and watch Claude undo what it just did.

- [ ] Press `Escape` twice to enter rewind mode

This opens up your conversation history, showing you every step you've taken.

When you're in rewind mode, you'll see a list of all your interactions. The current state is at the bottom. Earlier interactions are above it.

- [ ] Select a previous point in your conversation history

Use the arrow keys to navigate, then press `Enter` to select a point.

### Choosing What To Restore

- [ ] Review the three restore options that appear

When you select a point, Claude Code gives you three choices:

| Option | What It Does |
|--------|--------------|
| Restore code and conversation | Rewind your entire session to that point |
| Restore conversation only | Keep the conversation, but reset the code |
| Restore code only | Keep the code as-is, but rewind the conversation |

- [ ] Select "Restore code and conversation" to fully rewind

This is the most common choice. It takes you back to exactly how things were before that change was made.

- [ ] Exit rewind mode if you change your mind

Press `Escape` or select "Nevermind" to cancel and stay at your current point.

### Pausing And Resuming Sessions

- [ ] Quit Claude Code by pressing `Ctrl-C` twice

This stops your current session, but Claude remembers everything you did.

- [ ] Resume your exact session with the resume command

Claude Code outputs a command you can run to get back to where you were:

```txt
To resume this session, run:
claude resume <uuid>
```

Copy and run that command to pick up exactly where you left off.

Alternatively, press `Ctrl-C` twice again, then start a fresh session by typing `claude`.

- [ ] Use the `/resume` command to browse all your sessions

In a fresh Claude Code session, type `/resume` to see a list of all your previous conversations in this repository.

- [ ] Search through your sessions if you have many

You can type to filter the list and find the session you're looking for.

- [ ] Press `Enter` to jump back into that session

You're now back in your old session with all your code and conversation history intact.

### Testing Session Persistence

- [ ] Make a change to your codebase in Claude Code

Ask Claude to add or modify something.

- [ ] Exit with `Ctrl-C` twice

- [ ] Run `claude --continue` to resume your exact session

This is a shortcut that puts you right back where you were without needing to copy the UUID.

- [ ] Verify that your code and conversation are exactly as you left them

Both your code edits and your entire conversation history should be preserved.
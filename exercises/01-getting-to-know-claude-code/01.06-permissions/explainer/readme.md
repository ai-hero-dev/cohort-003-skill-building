# Permissions

## Introduction

When you're working with an agent, you need to think carefully about risk versus reward. Give Claude Code too much power, and it might accidentally delete your entire file system. That's why Claude Code has a detailed permissions model that's very strict by default about what it allows the agent to do.

You have complete control over what Claude Code can access. You can approve actions one at a time, create rules for entire categories of commands, and even share these permissions with your team so everyone gets the same safe setup.

## Steps To Complete

### Understanding the Permissions Flow

- [ ] Run a safe command with Claude Code

Ask Claude Code to run a safe command and observe that it executes immediately without asking for permission.

```
run echo hello
```

- [ ] Run a command that requires approval

Ask Claude Code to run a type check command. Notice that it now shows you:
  - The exact command it wants to run
  - The reason it wants to run it
  - Three options: approve this time, approve all similar commands, or deny

```
run a type check on the project
```

### Working with Permission Files

- [ ] Open `.claude/settings.local.json` in your project

This file stores all the permissions you've granted. Look for a `permissions` property with `allow` and `deny` arrays.

- [ ] Add a permission manually to the `allow` array

Edit the file directly to pre-approve a specific command. For example, add `pnpm type check` to automatically allow that command without asking.

- [ ] Test the permission you added

Ask Claude Code to run the command you just approved. It should execute without asking for permission.

```
run pnpm type check
```

### Creating Rules with Wildcards

- [ ] Allow all commands in a category using wildcards

Edit your `settings.local.json` to replace a specific command with a wildcard pattern. For example, change `pnpm type check` to `pnpm *` to allow all `pnpm` commands.

- [ ] Deny dangerous commands using the deny array

Add a command to the `deny` array to prevent Claude Code from running it. For example, add `bash git push` to block all git push commands, preventing accidental commits.

### Sharing Permissions with Your Team

- [ ] Rename `settings.local.json` to `settings.json`

This changes the file from local-only to shareable with your team.

- [ ] Commit the `settings.json` file to your repository

Now when any team member runs Claude Code on this project, it automatically picks up these shared permissions without having to set them up manually.

### Working with Web Permissions

- [ ] Ask Claude Code to fetch information from the web

Make a request that requires a web search. Claude Code will ask for permission to search the web.

```
fetch information about react-router-typegen from the web
```

- [ ] Grant web search permission and observe the results

When you approve, Claude Code will fetch the page and report back what it found. This permission also gets recorded in `settings.local.json`.
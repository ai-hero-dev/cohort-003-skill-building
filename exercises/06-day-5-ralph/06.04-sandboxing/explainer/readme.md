# Setting Up Claude Code in a Docker Sandbox

## Introduction

In the previous lesson, you felt the friction of running Ralph with human-in-the-loop mode. Claude was constantly pinging you for permission before running bash commands, fetching from websites, and doing anything else that might change your system.

To run Ralph autonomously, without you standing over it, those permission requests need to be handled automatically. But here's the problem: if we just skip all permissions, Claude can do strange things. AI agents aren't deterministic. They sometimes delete important files, break configurations, or generally cause chaos.

The solution is **Docker sandboxing**. It lets Claude Code run in an isolated environment where it literally can't reach the rest of your filesystem. It can still explore code, run commands, and work with git, but it's confined to a container. Permission requests become moot because the agent can only damage what's inside the sandbox.

## Steps To Complete

### Install Docker Desktop

- [ ] Download Docker Desktop for your machine from [https://docs.docker.com/get-started/get-docker/](https://docs.docker.com/get-started/get-docker/)

Choose the right version for your OS - Mac, Windows, or Linux.

- [ ] Install Docker Desktop and launch it

You may need to update to a more recent version if you already have it installed.


### Run Claude Code Inside a Docker Sandbox

- [ ] Open your terminal and navigate to a project directory you'd like to work in

- [ ] Run the Docker sandbox command:

```bash
docker sandbox run claude .
```

The period (`.`) means Claude Code will run inside a sandbox in your current directory.

- [ ] Wait for Docker to set up the sandbox

Docker will create a new sandbox environment (called something like `claude-cohort-003-project`) and pull down the latest version. This might take a minute or two on first run.

- [ ] Log in to Claude Code when prompted

Since you're in a fresh sandbox environment, Claude Code will ask you to set up as if it's your first time. Choose your theme preference and log in with your Anthropic subscription (or console account if you have one).

- [ ] Accept the safety check and choose your effort level

Claude will ask if you trust this folder. Say yes. Choose `medium effort` as your effort level for now.


### Test That Sandboxing Works

- [ ] Ask Claude Code to explore your codebase

Run this prompt in Claude Code:

```
Are we using npm or pnpm?
```

This is a lightweight exploration task that proves Claude Code is working normally inside the sandbox.

- [ ] Now test the sandbox boundary

Run this prompt in Claude Code:

```
Grab me a file from my Downloads folder in my home directory
```

Claude should respond that there is no Downloads directory in this environment because it's sandboxed. It won't have access to your local filesystem.

This is the safety layer working. Claude can see what it can't do and it tells you why.

- [ ] Exit the Claude Code process

When you're done testing, exit Claude Code. The sandbox will stop, but it stays configured and ready to use for the next lesson on running Ralph autonomously.
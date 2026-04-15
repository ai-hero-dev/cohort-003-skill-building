During the cohort, we used Docker Sandbox for running Claude Code in isolated environments. But I was honestly annoyed with how Docker Sandbox was implemented. It's unstable, changes all the time, and makes it really hard to do clever things like parallelizing or running an implementer followed by a reviewer.

So I built [Sandcastle](https://github.com/mattpocock/sandcastle) - an open source TypeScript library designed specifically for orchestrating AI coding agents in isolated sandboxes. It's more flexible, more stable, and gives you way more control.

In this lesson, you're going to migrate the Ralph loop from Docker Sandbox to Sandcastle. Your main script will shrink to just 17 lines of code.

## Steps To Complete

### Get the Sandcastle Branch

- [ ] Merge the `with-sandcastle` branch into your working branch

```
git merge with-sandcastle
```

This branch contains the drop-in replacement for the Ralph loop using Sandcastle.

You may end up with some merge conflicts. If you do, ask Claude to resolve them.

### Explore the New Structure

- [ ] Open `package.json` and verify that `@ai-hero/sandcastle` is listed as a dependency

Look for the `@ai-hero/sandcastle` package. I'm pushing development on this very quickly, so the version number will probably change.

- [ ] Check that a `.sandcastle` directory exists in your project root

This directory was created by running `sandcastle init` and contains your configuration.

- [ ] Open `.sandcastle/.env.example` to see what environment variables you need

If you want to use Sandcastle with Claude Code, you'll either need to pass an Anthropic API key or set up a subscription. You won't need a GitHub personal access token for this example until you connect the Ralph loop to GitHub issues.

### Understand the New Entry Point

- [ ] Open `src/main.ts` and read through the code

This is the new entry point for your Ralph loop. Notice how much simpler it is compared to the Docker Sandbox version. You should see roughly 17 lines of actual code.

```ts
import { run, claudeCode } from "@ai-hero/sandcastle";
import { docker } from "@ai-hero/sandcastle/sandboxes/docker";

const [, , planAndPrd, maxIterations] = process.argv;

await run({
  // Where your code runs (Docker, Podman, Vercel, Daytona, or custom)
  sandbox: docker(),
  // Which AI agent and model to use (claudeCode, pi, openCode, or codex)
  agent: claudeCode("claude-sonnet-4-6"),
  // The prompt file to use
  promptFile: `.sandcastle/sandcastle-prompt.md`,
  // The built-in Ralph loop limit
  maxIterations: Number(maxIterations) ?? 3,
  // Arguments to pass into the prompt
  promptArgs: {
    INPUTS: planAndPrd,
  },
  // Setup steps like running pnpm install when the sandbox is ready
  hooks: {
    onSandboxReady: [{ command: "pnpm install" }],
  },
});
```

- [ ] Look at the `.sandcastle/sandcastle-prompt.md` file

This file uses shell expansion syntax to run commands and inject their output into your prompt.

```md
<commits>

!`git log -n 5 --format="%H%n%ad%n%B---" --date=short 2>/dev/null || echo "No commits found"`

</commits>

<inputs>

{{ INPUTS }}

</inputs>

!`cat ralph/prompt.md`
```

Commands wrapped in `` !` `` are executed and their output replaces the command. The `{{ INPUTS }}` placeholder is replaced with the `promptArgs` from `main.ts`. So this prompt grabs the last five commits, injects your plan and PRD, and includes the Ralph prompt.

- [ ] Check the `Dockerfile` in the `.sandcastle` directory

Unlike Docker Sandbox, you can completely customize this Dockerfile. Notice what it installs: system dependencies like `jq`, `curl`, and `git`, the GitHub CLI, Node 22, `pnpm` support via corepack, and the Claude Code CLI.

### Build and Run Sandcastle

- [ ] Install dependencies in your project root

```
pnpm install
```

- [ ] Build the Docker image that Sandcastle will use

```
pnpm sandcastle docker build-image
```

This command builds the Dockerfile in your `.sandcastle` directory. The first build may take a while.

- [ ] Test the Ralph loop by running the afk.sh script

```
./afk.sh "your-plan-name your-prd-name" 3
```

Replace `your-plan-name` and `your-prd-name` with actual file names, and `3` with your desired number of iterations.

### Observe the Agent in Action

- [ ] Watch the logs as your agent runs

Control-click (or cmd-click on Mac) on the log output to see detailed information about what the agent is doing.

![Terminal showing Sandcastle log output with agent activity](./screenshot-1.png)

You'll see much more transparency compared to Docker Sandbox:

- The max iterations count and current iteration number
- Sandbox setup steps like `pnpm install`
- Expanded shell expressions from your prompt
- All agent logs and tool calls in real time

This is a massive improvement over Docker Sandbox, where all of this happened silently.

- [ ] Verify that the agent can work on your repository

Just like with Docker Sandbox, the agent should be able to modify files and commit its work. The difference is you now see everything it's doing.

### Troubleshoot and Share Feedback

- [ ] If you run into any issues, report them in the [Discord](https://aihero.dev/discord)

I'm actively developing Sandcastle and I'd love to know about any problems you encounter. Your feedback will help me improve this software.

- [ ] If Sandcastle works well for you, consider using it in your own projects

Sandcastle is open source and designed to be flexible. You can customize sandboxes, swap agents, and orchestrate complex multi-agent workflows - all things that are difficult or impossible with Docker Sandbox.

# Building a /do-work Skill

We've talked about the benefits of a `/do-work` skill, but understanding it theoretically is different from building one yourself. Now it's time to create your own `/do-work` skill using Claude Code.

A `/do-work` skill encapsulates the complete workflow for tackling a unit of work within your repository. It instructs the agent to plan the work, implement it, gather feedback through testing, and finally commit the code.

This teaches Claude Code to work methodically instead of just making changes in isolation.

## Steps To Complete

### Set Up Your Environment

- [ ] Open a Claude Code instance and navigate to your repository

You'll need an active Claude Code session with access to your codebase. Make sure you're in the correct repository where you want to add the new skill.

### Use the /write-a-skill Skill

- [ ] Use the `/write-a-skill` skill to create your `/do-work` skill

Invoke the `/write-a-skill` skill and provide a clear description of what you want the `/do-work` skill to do. Your prompt should specify that the skill should instruct the agent to:

1. Plan out the piece of work
2. Implement the work
3. Seek feedback through feedback loops using `pnpm type check` and `pnpm run test`
4. Commit the code as the final step

- [ ] Save the skill to your project repository, not your user settings

When Claude Code generates the skill, make sure it's saved to your project's skill directory (typically in the repository root) rather than your personal Claude Code settings. This ensures the skill is available to other team members and persists with your codebase.

### Review Your New Skill

- [ ] Examine the generated `/do-work` skill in your repository

Once Claude Code finishes writing the skill, review the structure and content to understand how it works. This is the skill you'll be putting into practice in the next lesson.
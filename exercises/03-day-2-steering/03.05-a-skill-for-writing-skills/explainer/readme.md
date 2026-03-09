# A Skill For Writing Skills

You've just learned what skills are and how they steer agent behavior. But understanding skills is one thing - building them is another.

So how do you actually build one? Use a skill to write skills.

Instead of learning skill structure in isolation, you're going to invoke the `write-a-skill` skill, use it to generate your first custom skill, and then immediately use that skill to solve a real problem. You'll see how well-structured skills empower Claude to do complex, multi-step work across your codebase.

For this exercise, you'll build a migration skill - one that moves code from Zod to Valibot. This isn't just practice. Once built, you'll have a reusable skill you can share across your organization to migrate multiple repositories.

## Steps To Complete

### Building Your First Skill

- [ ] Install the `write-a-skill` skill by running the command below

```sh
npx skills add mattpocock/skills/write-a-skill
```

Once installed, you'll be able to invoke this skill in Claude Code using `/write-a-skill`.


- [ ] Start a new Claude Code session

In this new session, you'll invoke the write-a-skill skill for the first time.


- [ ] Invoke the write-a-skill skill with a clear prompt

Type `/write-a-skill` in Claude Code and describe what you want: a skill that migrates code from Zod to Valibot. Tell the skill to research Valibot's API, understand the differences between Zod and Valibot, and create a deep, comprehensive skill that handles the common migration patterns. Mention that this skill should work across your organization's multiple repositories, not just this one.


- [ ] Review the generated skill

When the skill is generated, take a moment to read through its structure. Notice:
- How it breaks down the migration task into smaller steps
- Where it references external documentation or API differences
- How it's organized for Claude to understand what to do

This is what a well-formed skill looks like.

### Using Your New Skill

- [ ] Invoke your newly created Zod-to-Valibot migration skill on one file

Use the `/zod-to-valibot` skill (or whatever name was generated) to migrate at least one file in the repo from Zod to Valibot. This makes the skill real - you're not just building it, you're using it.


- [ ] (Optional) Migrate the entire repository

If you want to go further, invoke the skill again to migrate all Zod usage in the repository to Valibot. This is when you'll really see the power of a well-constructed skill - it should handle the full scope with minimal additional prompting.


- [ ] Verify the migration works

Test that the migrated code actually runs and behaves the same way it did before. You've now completed a full cycle: skill creation, skill invocation, and real-world results.
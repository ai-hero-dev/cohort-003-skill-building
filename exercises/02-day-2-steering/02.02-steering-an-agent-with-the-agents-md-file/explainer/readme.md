# Steering An Agent With The AGENTS.md File

Now you understand what an `AGENTS.md` file is. Time to try it out.

You're going to practice the real skill here: noticing a pattern the agent uses that you don't like, documenting it in `AGENTS.md`, and watching the agent adapt. This is the steering loop in action.

## Steps To Complete

### Understand the Bookmarks Feature

- [ ] Review the bookmarks feature you're about to build

This is a simple feature: users can bookmark lessons, and the system stores those bookmarks. It's straightforward enough that the agent can build it, but complex enough that you'll see the anti-patterns emerge.

### Run the Agent and Notice the Problem

- [ ] Run your agent in plan mode to build the bookmarks feature

Let the agent work without any steering guidance. Watch what it generates.

- [ ] Identify the positional parameters pattern

Look at the code the agent generated. You should see function calls using positional arguments instead of named parameters. For example:

```ts
// Positional parameters (what the agent might generate)
bookmarkLesson(userId, lessonId, timestamp);

// Named parameters (what you prefer)
bookmarkLesson({ userId, lessonId, timestamp });
```

Document what you see. Where does the agent use positional parameters? What function calls are affected?

### Add Steering to Your AGENTS.md File

- [ ] Run the `/memory` command from inside Claude

- [ ] Choose the local, project memory (not your global, user memory)

- [ ] Add a rule against positional parameters

Write a clear, specific rule. Something like:

```
## Code Style

When writing function calls, always use named parameters instead of positional arguments. This makes code more readable and maintainable.

Example:
- Instead of: `createBookmark(userId, lessonId, timestamp)`
- Use: `createBookmark({ userId, lessonId, timestamp })`
```

1. It saves the rule to your `AGENTS.md` file
2. It adds the rule to your agent context immediately, so you don't need to restart Claude

### Verify the Steering Worked

- [ ] Run the agent again on the same bookmarks feature

Now that you've added the rule to `AGENTS.md`, run the agent to build or rebuild the bookmarks feature.

- [ ] Compare the generated code

Look at the function calls in the new code. Are they using named parameters now? Did the agent listen to your steering?

If yes, you've successfully completed the steering loop. If no, refine your `AGENTS.md` rule and try again.

### (Optional) Find Your Own Anti-Pattern

If you want to go deeper, find another pattern in the codebase you'd like to steer against.

- [ ] Look for patterns you don't like

Consider these common agent anti-patterns:

- **`any` types in TypeScript** - the agent uses `any` as a shortcut instead of defining proper types
- **Missing error handling** - functions without try/catch blocks around async operations

- [ ] Pick one pattern and document it using `/memory`

Write a clear rule, similar to what you did for positional parameters.

- [ ] Test that the agent follows the new rule

Run the agent again. Does it respect the new steering?

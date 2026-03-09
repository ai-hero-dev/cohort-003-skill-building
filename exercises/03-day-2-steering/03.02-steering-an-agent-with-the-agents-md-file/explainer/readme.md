# Steering an Agent with the CLAUDE.md File

You know what `CLAUDE.md` files are. Now it's time to put one to work.

In this exercise, you're going to build a bookmarks feature for lessons. The codebase you're working with has some patterns baked into it that you probably don't want Claude to replicate.

Specifically, functions with multiple parameters of the same type use positional parameters instead of object parameters. This is easy to get wrong when calling the function, you could swap `userId` and `postId` and the code would still compile.

Your job is to steer Claude away from this pattern using your `CLAUDE.md` file.

## Steps To Complete

### Understand the Bookmarks Feature

- [ ] Read through the `plan.md` file provided below

This outlines what you're building: a simple bookmarks feature where students can bookmark lessons inline. Pay special attention to the files you'll need to create and modify.

### Run Claude Code Against the Plan

- [ ] Open a new Claude Code session

- [ ] Copy the entire `plan.md` file and paste it into Claude Code

Watch Claude work. As it explores the codebase and starts building, pay close attention to the code it generates. **Is it using positional parameters, or object parameters?**

### Add Your First Steering Rule to CLAUDE.md

- [ ] Create (or update) your `CLAUDE.md` file with the rule about function parameters

When you have a function with more than one parameter with the same type, use an object parameter instead of positional parameters:

```ts
// BAD
const addUserToPost = (userId: string, postId: string) => {};

// GOOD
const addUserToPost = (opts: { userId: string; postId: string }) => {};
```

### Test the Steering

- [ ] Use the `/memory` command to inject this rule into Claude's active context

This updates both your `CLAUDE.md` file and Claude's immediate context, so you won't need to restart the session.

- [ ] Ask Claude to regenerate or continue with the feature implementation

Watch whether Claude's new code follows the object parameter pattern. If it does, the steering worked.


### Find One More Anti-Pattern (Optional)

If you want to go deeper, look through the codebase and find one more pattern you'd like to steer against.

Here are some ideas:

- **`any` types in TypeScript** - The codebase already has some. Guide Claude to use proper types instead.
- **More positional parameters** - Are there other functions in the codebase using this pattern? Flag them.
- **Missing error handling** - Does the code assume happy paths? Add try/catch guidance.
- **Inconsistent naming** - Look for camelCase vs snake_case inconsistencies.

- [ ] Add your second steering rule to `CLAUDE.md`

- [ ] Inject it with `/memory` and test whether Claude respects it

### Verify the Feature Works

- [ ] Run the bookmarks feature locally (via `pnpm run dev` or your dev server)

- [ ] Log in as an enrolled student and navigate to a lesson

- [ ] Click the bookmark button in the metadata row and verify it toggles

- [ ] Check that bookmarked lessons show a filled bookmark icon in the course sidebar and course detail view

- [ ] Unbookmark a lesson and confirm the icon disappears everywhere

---

**The core skill here:** Notice a pattern the agent is using that you don't like. Write a rule in `CLAUDE.md` to steer it toward better behavior. Verify it worked. That's the loop you just completed.
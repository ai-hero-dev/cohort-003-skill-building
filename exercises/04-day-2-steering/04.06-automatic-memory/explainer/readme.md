So far we've been talking about skills and CLAUDE.md, but we haven't talked about Claude's automatic memory function. This shipped relatively recently at the time of recording, and what it does is allow Claude to steer itself over time.

## Finding Your Memory Files

We can discover this file by going into Claude Code and running a fresh instance, then using the `/memory` command.

```
/memory
```

When you press return on this, you can see that there are actually three types of memory:

| Memory Type    | Description                       |
| -------------- | --------------------------------- |
| User memory    | Your user CLAUDE.md               |
| Project memory | Checked in locally at CLAUDE.md   |
| OpenAutoMemory | Generated automatically by Claude |

![Showing the three types of memory](https://res.cloudinary.com/total-typescript/image/upload/v1773314849/ai-hero-images/zfurynpiy6ck4pkk1fj3.png)

## Exploring the Memory Folder

When you open the `memory` folder in VS Code, you might find it empty on some projects. However, on projects where Claude Code has been working more extensively, it will surface a `MEMORY.md` file.

Here's what Claude might write for me in that file, on a longer-running project:

```markdown
# Project Memory

## Effect ecosystem dependency management

- When installing new `@effect/*` packages, use `npm install --force` instead of `--legacy-peer-deps`. The `--legacy-peer-deps` flag corrupts the lockfile by removing existing `@effect/*` peer dependencies (e.g., `@effect/rpc`, `@effect/sql`, `@effect/experimental`).

## Testing patterns

- Tests use `@effect/vitest` with `it.effect()` for Effect-based tests.
- DB tests use PGlite with drizzle-kit/api `pushSchema` for schema setup.
```

This file gets put into the context alongside your CLAUDE.md file automatically.

## Should You Trust Automatic Memory?

This is still relatively new, so take a cautious approach. You should probably check on this file every so often just to make sure it's not adding weird cruft.

For instance, in the example above, the hint about `v.mock is hoisted` might not be necessary. Your LLM can probably figure that out on its own. Similarly, if `pushSchema` has already been deprecated in your repo, you want to get rid of that reference. In the video above, I delete several unused elements:

![Deleting the hint about @effect/platform](https://res.cloudinary.com/total-typescript/image/upload/v1773314850/ai-hero-images/ic4itnuugdoqshc4rglk.png)

## The Risk of Outdated Memory

The worst thing that could happen is the memory file goes out of date with the actual state of your repo. This is the thing to always worry about when you see memory-style systems.

**What to do:** Every couple of weeks, check inside your `MEMORY.md` file and see if there's stuff that might be conflicting with things you actually want your LLM to do. Remove anything that's no longer relevant to your project.

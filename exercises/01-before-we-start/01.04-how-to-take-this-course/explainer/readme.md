This course uses interactive exercises to teach you hands-on skills. Each exercise is set up so your repository starts in a specific state that matches the lesson.

You have powerful tools to manipulate your repo and get it exactly where it needs to be for each lesson. You'll use three main commands: `pnpm reset`, `pnpm cherry-pick`, and `pnpm pull`.

Each exercise page shows you a set of commits. These commits let you preview how the code changes throughout the lesson and help you jump to different starting points.

## Understanding Your Tools

| Command            | What it does                                | Best for                                           |
| ------------------ | ------------------------------------------- | -------------------------------------------------- |
| `pnpm reset`       | Resets your entire branch to match a commit | Starting fresh, guided learning                    |
| `pnpm cherry-pick` | Applies just the changes from one commit    | Keeping your own work while grabbing specific code |
| `pnpm pull`        | Updates your branch with the latest version | Staying in sync when the instructor makes fixes    |

### Reset vs Cherry-Pick

**Reset** is like a time machine. It resets your entire branch to match a specific commit, throwing away any work on that branch. This guarantees no merge conflicts, but you lose your local changes.

**Cherry-pick** is more surgical. It applies just the changes from a specific commit to your current work. This means you keep your code but might get merge conflicts if your code and the instructor's code touched the same areas.

## Key Things To Remember

When working on the main branch, you cannot reset it. You need to create a working branch first. You can call this branch anything you want, like `dev-branch`.

If you get merge conflicts after a cherry-pick, you can use Claude to help resolve them. Most conflicts from these exercises are straightforward to fix.

If you're not sure which commit to use, run `pnpm reset` and you'll get an interactive menu to choose from all available options.

## Steps To Complete

### Try Out Reset

- [ ] Navigate to the [Build a Feature](https://www.aihero.dev/workshops/day-1-claude-code-fundamentals-ju4au/build-a-feature~91339) exercise

You'll see a set of commits at the top of the page.

- [ ] Click the copy button next to the solution commit

Two options will appear: reset and cherry-pick.

![Copy button showing reset and cherry-pick options](https://res.cloudinary.com/total-typescript/image/upload/v1773400940/ai-hero-images/kbjnsxgmfgdmyujbh7r8.png)

- [ ] Select the reset option and copy the command

This will copy a command like `pnpm reset 03.04.01` to your clipboard.

- [ ] Create a new branch for your work

Run the following in your terminal:

```bash
git checkout -b dev-branch
```

- [ ] Paste and run the reset command in your terminal

Your branch will be reset to match the solution commit.

- [ ] Open `app/services/ratingService.ts` in your editor

You should see the rating service code that was added in the solution.

![rating-service.ts file showing the rating service code](https://res.cloudinary.com/total-typescript/image/upload/v1773400941/ai-hero-images/giqhskdrtvu5lizeh9mf.png)

- [ ] Switch back to the main branch

Run `git checkout main` and notice that the rating service file disappears, and shows with a strikethrough in the VSCode UI.

![File explorer showing rating-service.ts with a strikethrough, indicating it was removed](https://res.cloudinary.com/total-typescript/image/upload/v1773400942/ai-hero-images/wa2v762vxgfjksugrrqj.png)

### Try Out the Interactive Menu

- [ ] Run `pnpm reset` without any arguments

```bash
pnpm reset
```

An interactive menu will appear showing all available commits.

- [ ] Use the arrow keys to navigate the options

Press up and down to move through the list.

- [ ] Press Enter to select a commit

Your branch will reset to that state.

### Try Out Pull

- [ ] Make sure you're on your working branch

Run `git checkout dev-branch` if you're not already there.

- [ ] Run `pnpm pull` to get the latest changes

```bash
pnpm pull
```

This pulls in any updates I've made to the course materials.

- [ ] If you have any issues, ask in [Discord](https://aihero.dev/discord)

The community is there to help with any setup problems.

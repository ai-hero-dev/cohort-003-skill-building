I've always had some discomfort when it comes to multi-phase plans with AI. The issue is that human developers don't work that way.

![A multi-phase plan](https://res.cloudinary.com/total-typescript/image/upload/v1773384904/ai-hero-images/sm3roze51oi4cpr2ixbk.png)

When we understand the destination, we don't rigidly plan everything out in a single document. Instead, we create a Kanban board with different issues, some of which are blocked by others.

## Understanding Dependency Graphs

Think of it like this: some issues might have dependencies. For this issue to be completed, three other issues must be completed first.

![Diagram showing dependency graph with blocking relationships between issues](https://res.cloudinary.com/total-typescript/image/upload/v1773384905/ai-hero-images/byhh7cd302cvtdwqvd2j.png)

This dependency structure means that two developers can work on independent issues at the same time. Once those are done, they can both grab the next set of issues independently, and then one developer works on the final issue.

## Why Kanban Beats Multi-Phase Plans

| Aspect          | Multi-Phase Plan      | Kanban Board              |
| --------------- | --------------------- | ------------------------- |
| Flexibility     | Rigid, hard to modify | Easy to add new issues    |
| Parallelization | Sequential phases     | Independent parallel work |
| QA Integration  | Requires scheduling   | Grows naturally           |
| Scalability     | Hard to extend        | Infinitely extensible     |

A Kanban board is much less prescriptive than a multi-phase plan. If you want to add another issue, you just describe a blocking relationship. You haven't needed to change any other part of the plan.

In my experience, editing multi-phase plans is much harder. It's also really easy to QA because you just mark an issue as done, QA it, and add all the feedback as a separate issue. The graph grows naturally instead of forcing it into a plan.

![Adding a new issue to the dependency graph](https://res.cloudinary.com/total-typescript/image/upload/v1773384905/ai-hero-images/izbjzdngokdfybkcj9qw.png)

## The `/prd-to-issues` Skill

In the repo, I've replaced the `prd2plan` skill with my own `/prd-to-issues` skill. This breaks a PRD (which is probably already in GitHub) into independently grabbable GitHub issues using Vertical Slices and Tracer Bullets.

![The /prd-to-issues skill in the repository](https://res.cloudinary.com/total-typescript/image/upload/v1773384907/ai-hero-images/os0s6rv5bgeto6sre1uv.png)

### The `/prd-to-issues` Workflow

1. **Locate the PRD** - Find the PRD wherever it exists
2. **Explore the codebase** - Depending on context, explore what's needed
3. **Draft vertical slices** - Break the PRD into tracer bullets
4. **Categorize slices** - Mark them as either human-in-the-loop or AFK
5. **Create QA issue** - Generate a final issue with a detailed manual QA plan
6. **Quiz the user** - Ask if granularity and dependencies feel right
7. **Create GitHub issues** - Generate issues with blocking relationships

### Slice Categories

The skill distinguishes between two types of slices:

- **Human-in-the-loop slices** require human interaction such as an architectural decision or design review
- **AFK slices** can be implemented and merged without human interaction

The skill prefers AFK over human-in-the-loop where possible.

### The QA Plan

The skill always creates a final QA issue with a detailed manual QA plan for all items that require human verification. This is really nice because you can step away for a long time, and when you come back you've got an issue in GitHub with a detailed QA plan showing everything that's been done and what you need to verify.

![Instructions for creating a final QA issue with detailed manual QA plan](https://res.cloudinary.com/total-typescript/image/upload/v1773384908/ai-hero-images/kynfslpqbkbsgsjm18ie.png)

## Validation Questions

After presenting the proposed breakdown, the skill asks:

- Does the granularity feel right?
- Are the dependency relationships correct?
- Should you split any of them?
- Are the correct slices marked as human-in-the-loop or AFK?

![Validation questions in the /prd-to-issues skill](https://res.cloudinary.com/total-typescript/image/upload/v1773384908/ai-hero-images/kdyudwqtmo9fkl89bsea.png)

## Creating GitHub Issues

The skill creates GitHub issues using a fairly simple template:

```
- References the parent PRD in the issue number
- Has a "blocked by" section listing which issues must be completed first
```

All issues are passed into Ralph, so it should be able to see all the blocking relationships just by reading the text.

## Preventing Ralph from Human-in-the-Loop Tasks

Inside the Ralph prompt, I've made a small adjustment:

```txt
You will work on the AFK issues only, not the human-in-the-loop ones.
If all AFK tasks are complete, output <promise>NO MORE TASKS</promise>.
```

![Ralph prompt adjustment showing AFK-only instruction](https://res.cloudinary.com/total-typescript/image/upload/v1773384909/ai-hero-images/g53dakhtosufgkj0phad.png)

This prevents Ralph from doing the human-in-the-loop tasks. You may want to enforce this more deterministically by hiding them with labels, but for now this has worked fine.

## The Benefits

By using the Kanban approach instead of the plan approach, you get several advantages:

- **Parallel work** - You can independently pick out issues from the AI, parallelizing your work with the AI's work
- **Infinite extension** - You can extend the Kanban board infinitely by adding more QA issues
- **Better QA** - You get a really nice QA plan at the end

Next, we're going to use this new setup and see how it performs.

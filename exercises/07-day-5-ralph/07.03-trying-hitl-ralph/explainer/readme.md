# Trying HITL Ralph

You've learned what Ralph is conceptually. Now it's time to experience it firsthand.

Human-in-the-Loop (HITL) Ralph means you're watching the agent work and can step in if something goes off track. This is how you learn Ralph's behavior before you run it fully autonomous.

In this lesson, you'll use a pre-built prompt to guide Claude Code through building admin analytics features. You'll see the HITL loop in action: feed context, watch it work, observe what happens.

The goal: follow the admin analytics plan through phase one.

## Steps To Complete

### Set Up Your Environment

- [ ] Open a fresh terminal window

You may need to make the `ralph/once.sh` script executable first.

```bash
chmod +x ralph/once.sh
```

- [ ] Run the HITL Ralph command

Pass in the admin analytics plan and PRD to get started:

```bash
./ralph/once.sh "plans/admin-analytics-plan.md prd/admin-analytics.md"
```

This opens Claude Code with the prompt, plan, and recent commit history already loaded.


### Understand What You're Building

- [ ] Review the PRD that's now in your Claude Code session

The admin analytics feature exists because admins currently have no way to view platform-wide metrics. They have to visit each instructor's analytics page individually to understand overall platform health.

You're building a read-only analytics dashboard at `/admin/analytics` that shows platform-wide revenue and performance data visible only to admins.

- [ ] Check the plan structure

Notice how the plan breaks this down into phases. You're only working on phase one today.


### Run the HITL Loop

- [ ] Watch Claude Code explore the repository

It will read through the codebase to understand the structure. This is Ralph getting oriented.

- [ ] Observe what Claude Code does

Pay attention to how it approaches the problem. Notice:

- Which files it reads first
- How it interprets the plan and PRD
- What decisions it makes about implementation
- Where it might hesitate or take unexpected turns

- [ ] Follow the plan through phase one

Let Claude Code execute the work as outlined in the plan. Your job is to observe its behavior.


### Check Your Work

- [ ] Verify the phase one work is complete

Check that what was supposed to be built according to the plan has been implemented.

- [ ] Write down what you notice

Before moving to the next lesson, jot down:

- What did Claude Code do well in this loop?
- Where did it struggle or take unexpected turns?
- How did having the previous commits and plan in context help it stay on track?
- What would you change about the prompt if you ran this again?

These observations will help you understand HITL vs. AFK Ralph when you compare them next.
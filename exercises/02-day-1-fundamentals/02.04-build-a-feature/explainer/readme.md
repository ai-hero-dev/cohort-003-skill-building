# Build A Feature

You're about to build your first feature using an AI coding tool. You've explored the repo, understand the codebase, and now it's time to actually ship something.

This exercise is about getting hands-on with the AI tool without a detailed plan. You'll be observing how the AI naturally approaches the problem, staying aware of your context window usage, and building a course review system where students can leave reviews on courses.

## Steps To Complete

### Start With A Quick Prompt

- [ ] Write a 1-2 sentence description of what you want to build

Use a dictation tool if you have one. Just talk it out casually. You don't need a perfect plan before you start. The plan emerges through conversation with the AI.

Your prompt might look something like: "I want to build a course review system where students can submit reviews and see reviews from other students."

### Observe The AI's Natural Instincts

- [ ] Let the AI respond without steering it in any particular direction

At this stage, you're not customizing the approach or pushing back. Just observe what the AI naturally does.

Take notes on:
- How it breaks down the problem
- What architectural choices it makes
- What database schema it suggests

### Monitor Your Context Window

- [ ] Use the `/usage` command frequently to check how much context you've consumed

The `/usage` command shows you a UI displaying your token usage. There's a critical threshold to watch for.

You're in the "smart zone" when you're below 80,000 tokens (roughly 40% of the context window). Once you approach or exceed that, you're in the "dumb zone" where the AI's performance starts degrading.

Keep checking `/usage` throughout your entire build process.

### Build The Feature

- [ ] Once you feel confident the AI understands what you want, activate accept all edits mode

In Claude Code, press **shift+tab** to enable accept all edits mode. The AI will stop asking for confirmation on every file it writes and will start building the feature automatically.

### Test The Complete Flow

- [ ] Verify that students can submit a review

- [ ] Verify that reviews are saved properly

- [ ] Verify that reviews appear where they should

Test the entire end-to-end flow: submit, save, display.

### Debug With The AI

- [ ] If something breaks or doesn't work as expected, debug it in conversation with the AI

Testing and debugging are part of the normal feature build cycle. Work through issues together with the AI while continuing to monitor your context usage.

Stay in the smart zone. That's your priority throughout this entire process.
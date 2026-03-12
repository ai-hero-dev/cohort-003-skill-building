# Build a Feature

## Introduction

You've explored the codebase and understand how it's structured. Now it's time to build your first feature with Claude Code.

We're going to build a course review system where students can leave star ratings on courses. This feature is meaty enough to touch all areas of the codebase, but not so complex that the UI becomes overwhelming. The reviews will show as a simple 1-5 star rating on the courses list page and the course detail page.

Before diving in, understand that this isn't about building the perfect feature on your first try. It's about learning the workflow of prompting, observing what Claude naturally does, and iterating. You'll also learn to monitor your context usage as you build, watching for the "dumb zone" where token consumption starts degrading quality.

## Steps To Complete

### Starting Your Claude Code Session

- [ ] Open Claude Code in VS Code (or run `/clear` if you have an existing session)

This clears your conversation history so you start fresh.


- [ ] Write a lightweight prompt describing what you want to build

Keep it to 1-2 sentences. Something like:

```
I would like to create a course review system where students can review courses by leaving a star rating. We don't want to add written reviews, just star rating. These reviews will then be visible everywhere that courses are visible. We want to show the average rating on the courses in the list page and on the course page itself.
```

Don't overthink this. You're not writing a detailed specification, just enough to point Claude in the right direction.


### Observing Claude's Default Behavior

- [ ] Send your prompt and watch what Claude does next

Pay close attention to:

- Does it spawn an Explore sub-agent to understand the codebase?
- What files does it read first?
- What questions does it ask you?
- What's its overall approach?

Take notes. You're in observation mode, let Claude think out loud before you steer.


- [ ] Check your context usage with `/context`

You'll see a bar chart showing token consumption. Look for the main orchestrator agent's usage. Around 40% usage is when you should start getting nervous about running out of space.


### Reviewing Claude's Plan

- [ ] Wait for Claude to generate a plan and read it carefully

Claude will show you the steps it intends to take, the files it will touch, and how it will verify the feature works.


- [ ] Ask clarifying questions if needed

If something doesn't match your vision, push back. For example, if Claude suggests adding ratings to the dashboard but you don't want that, tell it. This is your chance to steer before implementation starts.


### Building the Feature

- [ ] Accept Claude's changes as it implements

Once you've reviewed the plan, you can flip to "accept all edits" mode (shift+tab cycles through submission modes). This lets Claude move faster without asking for permission on every file change.


- [ ] Keep watching `/context` as Claude works

If you're approaching 80K tokens (40% of the window), that's your signal to be more cautious. Ask Claude to summarize what's left or consider wrapping up the current phase.


- [ ] Wait for Claude to finish implementing all the steps

This includes database schema changes, service functions, route updates, and UI components. It will also run migrations and handle any setup commands.


### Testing the Full Feature

- [ ] Log into the dev UI as a student

Navigate to a course detail page. You should see a rating widget in the sidebar (if you're enrolled in the course).


- [ ] Submit a star rating by clicking on one of the stars

Watch for a toast notification confirming the rating was saved. The average rating display should update immediately.


- [ ] Change your rating by clicking a different star

Verify that the rating updates (upsert behavior) without errors.


- [ ] Visit the courses list page (`/courses`)

You should see the average rating displayed on course cards next to the instructor name, formatted as a filled star icon followed by the rating and count.


- [ ] Test as different user types

Log in as a non-enrolled user and verify you see the rating display but no widget to submit. Log in as an instructor and verify you don't see a rating widget on your own course.


### Debugging if Things Break

- [ ] If something doesn't work, describe the issue to Claude in plain language

Rather than trying to fix it yourself, tell Claude what you expected to happen and what actually happened. Stay in conversation with the AI, it's part of the natural build cycle.


- [ ] Run `/context` again to check how much space you have left

If you're running low, you might need to wrap up or start a fresh session for the next phase of work.
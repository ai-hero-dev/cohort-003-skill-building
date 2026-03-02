# Codebase Exploration

## Introduction

LLMs are stateless. Every time you interact with an agent, it's like hiring a brand new developer who's never seen your codebase before. This means exploration isn't a one-time setup task - it's the foundation of every single agent interaction.

You can use agents to explore unfamiliar codebases faster than you could manually. You'll learn to ask the right questions, spot patterns, and understand architecture through the agent's eyes. This skill unlocks everything else in the course.

## Steps To Complete

### Exploring the Repository

- [ ] Open VS Code and run Claude Code in the terminal

Use the same prompt structure shown in the transcript:

```
Tell me what the tech stack of this repo is and what its intended purpose is.
```

- [ ] Watch for sub-agent activity in the Claude Code interface

Notice when Claude is exploring files or running commands. This is the agent "thinking out loud" as it discovers the codebase structure.

### Digging Deeper

- [ ] Ask follow-up questions based on Claude's initial response

Here are some angles to explore:

```
How does PPP (Purchasing Power Parity) work in this repo?
```

```
What user roles and permission levels exist in this application?
```

```
Where is the authentication and authorization logic?
```

```
How does the React Router setup work specifically?
```

```
What does the database schema look like?
```

- [ ] Keep track of what questions Claude asks itself

The agent might need to check multiple files or run commands like `tree` to understand structure. Notice when it does this.

### Finding Hidden Details

- [ ] Ask Claude to determine which React Router mode this app uses

The codebase uses React Router, which has three different modes. Can Claude figure out which one? What clues did it look for?

```
Which React Router mode is this app using, and how can you tell from the codebase?
```

- [ ] Ask Claude about user roles and capabilities in the application

This requires understanding both the code structure and the business logic. What user types can you identify?

```
What user roles and capabilities does this application support?
```

### Validating Your Understanding

- [ ] Review what you've learned and write down:

- The main purpose of this application
- Key technologies in the tech stack
- How users and permissions are structured
- Which React Router mode is being used and why that matters
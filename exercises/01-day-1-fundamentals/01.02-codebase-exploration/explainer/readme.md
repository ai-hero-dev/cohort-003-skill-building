# Codebase Exploration

Every time an agent interacts with your codebase, it starts from scratch. There's no memory of previous explorations, no accumulated context. This means **exploration becomes the foundational skill** for everything agents do.

Before an agent can refactor code, add features, or fix bugs, it needs to understand what it's looking at. This exercise teaches you how to guide agents through unfamiliar codebases, and how to use that same process to deepen your own understanding.

Agents read code like you do. They look at file structure, read key files, and build mental maps of the architecture. This means good naming conventions and clear file organization aren't just nice for humans, they're critical for agent performance too.

## Steps To Complete

### Explore the Project Structure

- [ ] Ask the agent to give you a rundown of the tech stack and main purpose of the repository

Start broad. What technologies are being used? What problem does this codebase solve? What are the key entry points?

- [ ] Ask the agent to map out the file structure and identify the most important files

Have it explain why certain files matter more than others. Good file naming should make this obvious.

- [ ] Ask the agent to identify the main architectural patterns being used

Look for how code is organized - is it component-based? Layer-based? Domain-driven?

### Investigate React Router

- [ ] Use the agent to research React Router's three different modes: Data, Framework, and Declarative

The agent can search the web for this. You're combining codebase knowledge with external documentation.

- [ ] Have the agent determine which React Router mode is being used in this project

This is where you'll focus your exploration. Look at the code patterns, configuration, and file structure. Which mode matches what you see?

- [ ] Document the evidence that led to your conclusion

What specific files or patterns made it clear which mode is in use?

### Understand User Roles and Permissions

- [ ] Ask the agent to identify all the different user roles in the application

Who can do what? Are there admin users, regular users, guests?

- [ ] Trace how permissions flow through the codebase

How does the system check if a user is allowed to perform an action? What components or files handle this?

- [ ] Map out the capabilities available to each role

Create a simple table showing which roles have access to which features.

### Learn How PPP Works

- [ ] Ask the agent what PPP stands for in the context of this codebase

It's a specific business logic pattern. The agent should find where it's implemented.

- [ ] Identify the files and functions responsible for PPP logic

Where in the code does this feature actually work?

- [ ] Explain how PPP integrates with the user roles and permissions system

How do these pieces connect?

### Reflect on the Exploration Process

- [ ] Look back at your exploration steps

What questions did you ask? In what order? Did you get answers efficiently?

- [ ] Note which parts of the codebase were easy to understand and which were confusing

How much did file naming and structure help or hurt?

- [ ] Think about how an agent with poor tool descriptions or weak system prompts might struggle

What would go wrong if the agent didn't know which files to prioritize?
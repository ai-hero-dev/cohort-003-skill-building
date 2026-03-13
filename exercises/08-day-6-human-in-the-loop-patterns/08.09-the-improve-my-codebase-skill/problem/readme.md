# The Improve My Codebase Skill

## Introduction

We know that deep modules improve code quality and make it easier for AI to navigate. But turning a bad codebase into a good one requires a concrete process.

The `/improve-codebase-architecture` skill walks through your code base and finds opportunities to deepen it. It identifies clusters of shallow modules that should be merged, designs multiple interface options for you to choose from, and creates a GitHub issue with a refactor plan.

In this lesson, you'll run the skill on your own codebase and see how it applies everything we've learned about interfaces, modules, and architectural friction.

## Steps To Complete

- [ ] Run the `/improve-codebase-architecture` skill

```
/improve-codebase-architecture
```

The skill will explore your codebase and present architectural candidates. Let it run to completion.


- [ ] Review the exploration results

The skill will identify clusters of shallow modules and explain why they're coupled together. Look for patterns like:

- Understanding one concept requires bouncing between multiple small files
- Modules with interfaces nearly as complex as their implementation
- Pure functions extracted just for testability, but bugs hide in how they're called
- Tightly coupled modules creating integration risk at their seams

Pick whichever candidate resonates most with your codebase.


- [ ] Accept the skill's recommendation or choose your own candidate

The skill will ask which deepening opportunity you'd like to explore. Either follow its recommendation or select a different candidate if you have your own architectural concern in mind.


- [ ] Let the skill design multiple interfaces

The skill will spawn multiple sub-agents in parallel, each producing a radically different interface design. This gives you diverse options to choose from.


- [ ] Review the interface designs

You'll see 3 different approaches. Each one trades off complexity, testability, and caller convenience differently. Think about which design best matches your codebase's needs.


- [ ] Accept the skill's recommendation or choose your own design

The skill will recommend which interface it thinks is strongest and why. You can accept it or ask for a different design.


- [ ] Create the GitHub issue

```
Yes
```

The skill will create a GitHub issue with the refactor RFC. This becomes your backlog item that Ralph can work on, or a HITL task you can tackle yourself.


- [ ] Compare your notes with the solution

Once you've run the skill and created your issue, check the solution folder to see what the instructor found in the same codebase. Your architectural instincts might differ, and that's completely fine, architecture is about taste.
The solution to fixing a bad codebase requires a human working alongside an AI, using the `/improve-codebase-architecture` skill to find opportunities for deepening modules within the codebase.

But if that's the cure, how do you prevent a codebase from going bad in the first place?

The key is to build **module awareness** into your planning from the start, especially when planning large features outlined in a PRD.

## Updating the Write a PRD Skill

The `/write-a-prd` skill has been enhanced with an additional section that brings module-first thinking into the planning process:

| Step | Action                                                                                  |
| ---- | --------------------------------------------------------------------------------------- |
| 1    | Sketch out the major modules you will need to build or modify                           |
| 2    | Actively look for opportunities to extract deep modules that can be tested in isolation |
| 3    | Check with the user that these modules match their expectations                         |
| 4    | Check which modules they want tests written for and at what boundary                    |

![The /write-a-prd skill showing the new section added before section five](https://res.cloudinary.com/total-typescript/image/upload/v1773395293/ai-hero-images/stlcqyb5k5o4sjhhrxxp.png)

A deep module encapsulates a lot of functionality in a simple, testable interface which rarely changes. This is the architectural ideal you should be aiming for.

## Bringing Modules Into the Process

By building this module awareness into your PRD, it naturally flows into your implementation decisions. You'll find yourself documenting:

- The modules that will be built or modified
- The interfaces of those modules that will change

This brings modules and interfaces directly into the planning process, rather than discovering architectural problems after implementation begins.

## Next Steps

Feel free to use the updated `/write-a-prd` skill to try something out in your codebase. Or jump into the [Discord](https://aihero.dev/discord) to discuss how you might improve this skill even further and bring your own architectural knowledge into how you like to build codebases.

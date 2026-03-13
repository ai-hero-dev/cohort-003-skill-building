When AI looks at a poorly organized codebase, it sees something like this:

![Bad codebase structure](https://res.cloudinary.com/total-typescript/image/upload/v1773388804/ai-hero-images/feasws0qmdgvxsbt9cay.png)

Dozens and dozens of modules, each with exported functions and internal functionality scattered throughout. To understand where specific code lives, AI must trace through the entire import-export chain across multiple files.

This creates a fundamental problem: **AI can't understand at a glance where to find specific functionality.**

## Why This Matters for Testing

These tiny chunks make it nearly impossible to get good tests. If you want to test a module, you have to test it in isolation:

- Test module A on its own
- Test module B on its own
- Test module C on its own

![Diagram showing fragmented modules that are difficult to test](https://res.cloudinary.com/total-typescript/image/upload/v1773388806/ai-hero-images/yoa7asgxdvjlg6h1u067.png)

**You don't get a good sense for how all the pieces work together.** When one module changes, its tests break because they're too tightly coupled to that module's internal shape.

We know how important good feedback loops are for AI. Fragmented codebases destroy those loops.

## Humans Have an Advantage AI Doesn't (Yet)

As a human developer, you can navigate a bad codebase reasonably well. You develop instincts about the code over time. You learn that:

- These files relate to authentication
- Those files are the API layer
- This group of components handles a specific feature
- That group handles a different feature

But AI doesn't have the same advantage. **It can't develop memories about a codebase the way you can.** Every time it encounters a bad codebase, it has to recreate all the relationships from scratch.

## Deep Modules: The Solution

How do we fix this? We restructure code into **larger, more meaningful chunks** and bake the intention of the code directly into its structure.

This concept comes from John Ousterhout's ["A Philosophy of Software Design"](https://www.amazon.co.uk/Philosophy-Software-Design-2nd/dp/173210221X/ref=asc_df_173210221X?mcid=4ad72ffa15c63e048dc7c7dfb141e124&th=1&psc=1&tag=googshopuk-21&linkCode=df0&hvadid=697235261482&hvpos=&hvnetw=g&hvrand=8711332229051218017&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9045977&hvtargid=pla-1587146939672&psc=1&hvocijid=8711332229051218017-173210221X) and is called **deep modules.**

A deep module has two parts:

| Part               | Description                                              |
| ------------------ | -------------------------------------------------------- |
| **Interface**      | A thin barrier defining how other code calls this module |
| **Implementation** | Everything hidden behind that simple interface           |

On the interface, you define:

- Which functions or methods are available
- How to call each one
- Which properties are exposed
- How they work together

Behind the interface, you stack as much implementation as possible. **The more implementation you can hide behind a simple interface, the better.** This means:

- Different parts of your system only depend on the public interface
- That interface rarely changes
- You can write tests for huge units individually
- Those tests won't break when internal implementation details change
- You can deeply experiment inside the module without affecting other code

## How AI Benefits

When your codebase has deep modules with simple interfaces, AI can **read the interface and immediately understand what the module does.** From a high level, it quickly grasps the entire codebase's purpose and exactly where it needs to make changes:

![Deep modules architecture](https://res.cloudinary.com/total-typescript/image/upload/v1773388807/ai-hero-images/jubcmspnundqq1kxqjut.png)

This transforms how effectively AI can work with your code.

## The Cognitive Load Problem

There's another massive bonus: **this approach dramatically decreases cognitive load on the developer.**

When you're maintaining a system where AI is constantly moving code around and changing implementations, keeping the internal map in your head becomes exhausting. This cognitive burden is something many developers feel acutely when using AI tools.

Any strategy that reduces this cognitive load makes your life easier. Deep modules deliver on this promise.

When you structure your code this way, something interesting happens:

- **You** focus on designing interfaces and how modules interact
- **AI** handles most of the implementation details
- **You** spend less time reviewing internal code, more time reading tests
- **The code** functions as "grey boxes" - not fully black boxes (you can look inside), but by default, you trust AI to handle the implementation

You become an architect and interface designer while AI becomes the implementation specialist.

## A Real-World Example

I build all my content on custom video editing software. Imagine the complexity:

- A frontend with multiple modules including state management reducers and selectors
- A complex backend API spread across about 20 interrelated files
- A CLI tool that monitors files created by OBS and detects silence
- Local database modules for saving data

![Video editor modules separated](https://res.cloudinary.com/total-typescript/image/upload/v1773388807/ai-hero-images/mspjpmzydivowbgqmnes.png)

The problem? Bugs kept appearing at the seams between these systems. A bug might look like it's in the backend, but actually it was how the frontend called the backend API. Or the backend wasn't calling the CLI properly.

Finding bugs meant debugging across all four system boundaries. The solution was to **wrap the entire thing as a single service:**

![Video editor as a service](https://res.cloudinary.com/total-typescript/image/upload/v1773388808/ai-hero-images/l45snijmocroc3ozsiqz.png)

The service had two parts:

1. An SDK callable from the frontend
2. An API handler on the backend that receives messages from that SDK

This transformed the entire system into one deep module:

Now whenever something breaks, I can write an integration test that tests the entire flow end-to-end. I don't need to care about the internal structure anymore.

## The Human Element

Identifying that this was a problem, and discovering that wrapping it all in a service was the solution? **That required human insight.** AI isn't capable of this kind of architectural thinking yet, at least not without human guidance.

This means **you need to develop the language to talk about deep modules with AI.** Designing your codebase for deep modules needs to be embedded in your planning process from the start.

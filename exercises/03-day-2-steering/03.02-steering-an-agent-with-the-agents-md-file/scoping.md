A: Go

Q: Looking at this lesson within the **Day 2: Steering** section, I can see the arc clearly:

- **02.01** introduces what an AGENTS.md file *is*
- **02.02** (this lesson) teaches how to *use* it to steer an agent's behavior
- **02.03-02.04** move into agent skills and writing them

So this lesson sits in the "application" layer — the learner already knows AGENTS.md exists, and now they need to see it in action solving a real problem.

The current prompt mentions:
> "Create a situation where an agent makes poor decisions, then steer it with an AGENTS.md file to enforce better patterns."

**Here's my read:** This is actually pretty well-scoped as a concept, but I need to understand the intent better. 

Let me ask the clarifying questions:

1. **What's the core takeaway?** After this lesson, should the learner be able to: "Write an AGENTS.md file that fixes specific agent anti-patterns"? Or is it more about "Diagnosing when an agent needs steering and knowing what lever to pull"?

2. **About the bookmarks feature specifically** — is that the *vehicle* for teaching (a concrete example where agents naturally go wrong), or is it the *lesson content itself*? Because if it's the latter, the scope might be too broad.

3. **What "poor decisions" are we steering against?** The prompt mentions "positional parameters" — but I want to know: Are we teaching learners to use AGENTS.md to enforce *coding style decisions*, or *architectural decisions*, or *API design decisions*? That changes the scope significantly.

Which of these feels like the real learning outcome to you?

A: Yeah the bookmarks feature is a vehicle for teaching and the poor decisions we're sort of prompting users to say, "Okay positional parameters is the one." Like this is definitely an exercise. We're trying to teach skills here not knowledge.

The core takeaway is we've sort of understood what agents.mt is and this is more like a playground for using it to steer an agent's behavior. We're kind of training them to do that or giving them an opportunity to do the thing where you notice something that the agent does that you don't like and they ping it into the agents.mt file. Positional parameters is kind of the one that the code base has been tailored to support, I think. That's the one but we should also prompt them to find others that they might be interested in changing and updating.

Q: Okay, this clicks for me now. **This is a hands-on playground lesson, not a knowledge dump.** The learner is practicing the *skill* of "notice bad pattern → fix it in AGENTS.md → verify it works."

I have a few scoping questions to lock this down:

1. **The discovery phase** — Are we asking learners to run the agent cold and *organically notice* the positional parameter anti-pattern? Or do we guide them to it? (My instinct: guide them to it for lesson 1, because if they miss it, the lesson stalls. Organic discovery feels like a bonus.)

2. **The feedback loop** — How do learners verify the agent actually *listened*? Do we:
   - Have them run the agent again and watch the output?
   - Have them inspect generated code directly?
   - Run some kind of lint/check?
   
   This matters because it defines how long the lesson actually is.

3. **The "find your own" part** — This feels like it could balloon the scope. Are we asking them to:
   - Find *one more* anti-pattern and steer against it?
   - Find multiple and pick one?
   - Just document what they *could* steer without actually doing it?
   
   Or should that be a separate "advanced" activity?

4. **Codebase assumptions** — The bookmarks feature is the vehicle. Do we build it from scratch in this lesson, or does it already exist and learners just work with it? (If build-from-scratch, that's a lot of scaffolding that distracts from the AGENTS.md practice.)

Which of these decisions do you already have answers for?

A: Yeah we definitely guide them to it. We essentially want to create steps to complete outcome here where:
1. The first step is to understand the other thing that we're building here.
2. Then we get them to run it and notice if the agent does any positional parameters (yeah you're right).
3. Then there's the feedback loop thing so they discover it or we say, "Okay now's the time to put some agents.md stuff in," or we could even use the /memory command too, which would not only put it in the agents.md immediately but would also put it in the agents context so they wouldn't need to restart Claude.
The find your own part, I suppose we do want to get them to find one more anti-pattern and maybe we should give them ideas for what that could be. The code base, at this point they've already done plan mode, right, so we're going to be using plan mode with this too. Maybe this is a chance to sort of re-look at plan mode a little bit. They're doing their usual loop; they're just adding in a little bit of extra stuff into it. We do need a sort of testing step at the end as well to say, "Okay this is what the feature you're building should look like at the end." The most important thing is that they've found something in the code base that they don't like and have written an agents.md file for it.

Q: Alright, I'm seeing the shape of this now, and I want to push back on one thing before we lock scope.

You've got:
1. Understand the bookmarks feature
2. Run the agent, notice positional params
3. Add to AGENTS.md (with /memory shortcut option)
4. Find one more anti-pattern + provide ideas
5. Re-practice plan mode with the steering addition
6. Test the final feature

**That's a lot for one lesson.** Here's my concern: Steps 1-3 are the core skill (notice pattern → steer it). But steps 4-6 keep expanding the scope. By the time they get to "find your own," they're context-switching from "learning to steer" to "becoming a code critic," and the lesson loses its tight focus.

Here's how I'd split it:

**This lesson (02.02)**: The tight, guided path
- Understand the bookmarks feature (quick overview, not build-from-scratch)
- Run agent, guide them to spot positional params
- Add to AGENTS.md via /memory
- Verify it worked (re-run, see the diff)
- **Done.** They've completed the steering loop once.

**Then 02.03 or later**: Finding your own anti-pattern + testing becomes its own exercise, maybe even after they learn skills (02.03-02.04).

The reason: **The core skill is the steering loop itself.** Once they nail that once, they can repeat it. Adding the "find your own" in the same lesson makes them solve two problems: "How do I steer?" AND "What should I steer against?" That's cognitively expensive.

Does that feel like scope-creep to you, or are those steps genuinely all equally important for this lesson?

A: I think the key here is to make the "find your own" optional, which I sort of think of as being two types of learners:
- The types who want direction
- The ones who want to go off and do their own thing and experiment, the more self-directed ones
I think the optional would be to find your own and I think we give them some inspiration. Do you have any ideas of what, I mean, we'll be in a TypeScript and Node code base? Do you have any ideas of what they could steer against?

Q: Good call making it optional — that's a solid way to honor both learner types without bloating the core lesson.

For a TypeScript/Node codebase, here are some natural anti-patterns agents tend to fall into:

**Common ones I'd suggest:**
- **Magic numbers/strings** — Agents hardcode values instead of extracting constants
- **Missing error handling** — They write happy-path code without try/catch
- **Type safety shortcuts** — Using `any` instead of proper types, or skipping interface definitions
- **Naming conventions** — Inconsistent variable naming (camelCase vs snake_case, unclear abbreviations)
- **Console.log debugging** — Leaving debug statements in production code
- **Async/await inconsistency** — Mixing promises and callbacks, or forgetting awaits

**My instinct?** I'd surface **2-3 options maximum** and frame them as "Here are patterns we've noticed — pick one if you want to go deeper." Otherwise you're creating decision paralysis.

**But before I list them in the lesson,** I want to know: **Has the codebase already developed a "style" through earlier lessons?** Like, are there established patterns in the code the learner built on Day 1 that they'd recognize? If yes, surfacing anti-patterns *against those patterns* would be more resonant than generic ones.

What patterns have they been building with so far?

A: Yeah the code base already has developed a style. They start from a code base that's like 20,000 lines long and they will, by this point, have developed a style. Positional parameters is a big one and probably any's in TypeScript. There are some stuff in the code base which has any in it. That's probably the big one.

Q: Perfect. **Then the "find your own" inspiration list should be super concrete and rooted in what they've already seen:**

- "Look for `any` types in the codebase — the agent might use them as a shortcut instead of proper types"
- "Check if there are other places where the agent uses positional parameters (beyond what we just fixed)"
- "Look for functions without error handling — guide the agent to add try/catch patterns"

These aren't abstract patterns — they're things *already in the codebase* they can literally point to and say "I don't want this style here either."

That grounds the optional challenge in reality and makes it feel like a natural extension of what they just learned, not a separate exercise.

---

Okay, I think I have enough to scope this. **One last boundary question before I write the summary:**

**The testing step you mentioned** — "This is what the feature you're building should look like at the end" — is that:
- A manual check (they run the bookmarks feature and verify it works)?
- An automated test they run?
- Just a visual inspection of the generated code?

And should that testing happen *before* they tackle the optional challenge, or is it part of the wrap-up after everything?
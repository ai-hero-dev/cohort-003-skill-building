The `/improve-codebase-architecture` skill starts by scanning your entire codebase to understand its structure and find places where the code could benefit from deeper modularization.

![Terminal showing the /improve-codebase-architecture skill starting its exploration](https://res.cloudinary.com/total-typescript/image/upload/v1773395111/ai-hero-images/qpm8efipembnm7pkq2tn.png)

Once the skill completes its analysis, it returns several options for architectural improvements. Each option identifies a group of services or modules that could be consolidated into a deeper, more cohesive unit.

![List of five architectural deepening opportunities displayed in the terminal](https://res.cloudinary.com/total-typescript/image/upload/v1773395112/ai-hero-images/go1bs5b7pxffmspy8yyw.png)

The skill found five opportunities. Let's look at the first one: the quiz subsystem.

### Option 1: Quiz Subsystem

This option suggests merging the quiz scoring, quiz CRUD operations, and XP awarding into a single deep module.

The reason this matters is that the current quiz scoring service uses raw database calls instead of using the ORM that exists elsewhere in the codebase. It has `any` types scattered throughout and lacks test coverage. It reads like code written by someone unfamiliar with the codebase conventions.

By consolidating these three services into one deep module, you get:

- A single, testable boundary for all quiz operations
- Elimination of the raw database drift (no more mixing BetterSQLite3 raw SQL with Drizzle ORM)
- Clearer separation of concerns

Some of the architectural recommendations use specialized terminology: terms like "side effects," "transactional domain operations," and "monoliths." If you're not familiar with these phrases, ask the LLM directly what they mean. Learning this vocabulary pays dividends later, you'll be able to use these same phrases when prompting the LLM with improvements to your own codebases.

## Asking for a recommendation

You can ask the LLM which option it recommends. Think of it like asking a waiter which meal they prefer most.

The recommendation comes back: option 1. The reason is clear - it's the only place in the codebase mixing raw BetterSQLite3 SQL with Drizzle ORM. That inconsistency is a bug vector.

![User asking the LLM which option to explore, with the LLM recommending option 1](https://res.cloudinary.com/total-typescript/image/upload/v1773395113/ai-hero-images/zm589cjdrej8anp8pqzh.png)

## Exploring the chosen option

Once you've picked an option, the skill spawns multiple design agents to propose different interface designs. Each agent approaches the problem from a different angle: one with a minimal interface, one with a flexible interface, and one optimized for callers.

![Terminal showing three design agents being spawned to create interface alternatives](https://res.cloudinary.com/total-typescript/image/upload/v1773395114/ai-hero-images/yhazp3xowafjupdxjmrm.png)

Interface design is a deep topic. You get better at it the more systems you design. Seeing multiple options from the AI is incredibly valuable for developing taste in design. You don't need to get it perfectly right on the first pass - you can always run `/improve-codebase-architecture` again later and target the same component to make improvements.

## Comparing the designs

Before diving into the detailed designs, you can ask the LLM which design it recommends. The LLM recommends Design B:

![Terminal showing the LLM recommending Design B](https://res.cloudinary.com/total-typescript/image/upload/v1773395114/ai-hero-images/dkaotiqmoomcux5zv0vq.png)

Let's examine what it looks like:

**Design B uses a factory pattern with dependency injection:**

```typescript
const quiz = createQuizModule({
  db?,
  scoringStrategy?,
  quizPassXp?
});
```

The module exposes these methods:

| Method                                       | Purpose                               |
| -------------------------------------------- | ------------------------------------- |
| `getQuizForLesson(lessonId)`                 | Fetch a quiz for a lesson             |
| `getBestAttempt(userId, quizId)`             | Get the student's best attempt        |
| `getLatestAttempt(userId, quizId)`           | Get the student's most recent attempt |
| `getAttemptHistory(userId, quizId)`          | Get all attempts for a quiz           |
| `getStats(quizId)`                           | Get aggregated quiz statistics        |
| `submitAttempt({ userId, quizId, answers })` | Submit a quiz attempt                 |
| `saveQuiz({ lessonId, title, ... })`         | Create or update a quiz               |
| `deleteQuiz(quizId)`                         | Delete a quiz                         |

This design has several advantages:

- The factory pattern prevents raw SQL drift. Tests inject an in-memory database directly - no mocking hacks needed.
- All quiz concerns live behind roughly 8 methods.
- Whether you're an instructor creating a quiz or a student taking it, you're calling the same module. All quiz logic is in one place.
- The XP amount is completely configurable from outside. The module doesn't own the XP value - it's just a parameter.

## Before and after

The GitHub issue shows a clear before-and-after comparison of how callers use these functions.

![GitHub issue showing the before-and-after comparison of caller code](https://res.cloudinary.com/total-typescript/image/upload/v1773395115/ai-hero-images/r3lotzbmoaehrdhxzh4p.png)

**Before:** Multiple service calls scattered across your routes:

1. Grab the quiz by lesson ID
2. Grab the quiz with its questions
3. Get the best attempt
4. Compute the quiz result
5. Award XP

**After:** Just two calls in most cases:

```typescript
// In the loader:
const quiz = await quizModule.getQuizForLesson(lessonId);
if (quiz) {
  const attempt = await quizModule.getBestAttempt(userId, quizId);
}

// In the action:
await quizModule.submitAttempt({ userId, quizId, answers });
```

## Small changes, big payoff

This is a relatively small change - you're just combining functionality into a larger testable unit. But over time, as you apply this pattern repeatedly and bake this thinking into your planning, your codebase becomes:

- More testable
- Easier to navigate
- Better able to support stronger feedback loops

You could even turn this quiz module into a "gray box." As a user of the module, you test it entirely from the outside. You don't need to worry about what's inside. As long as the XP gets awarded, the quiz gets passed, and all those functions work correctly, you're good.

## Creating the issue

The skill offers to create a GitHub issue with the recommended design. This gives you a concrete specification to work from when you're ready to implement.

The skill makes architectural patterns more concrete and actionable. Feel free to grab this skill and run it on your own codebases to see what comes out.

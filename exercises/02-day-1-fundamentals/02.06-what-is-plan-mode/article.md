# An Introduction To Plan Mode

This article is for anyone who's used an AI coding agent and been frustrated by the results.

If you've ever felt that your AI agent produces low quality code, or doesn't understand your codebase, you need to try plan mode.

In plan mode, you iterate with the agent on what you want to build before any code gets written. You discuss requirements, validate assumptions, and refine your approach. The agent explores your codebase and builds context. By the time you start coding, the agent knows exactly what to do and has all the information it needs.

I'll be using [Claude Code](https://docs.anthropic.com/en/docs/claude-code/overview) examples throughout this article - it's where I first discovered plan mode. But plan mode has been added to other AI coding agents too. Check your tool's documentation to see if it's supported.

## What Is Plan Mode?

When you start Claude Code with `--permission-mode plan`, or type `/plan` in a session, you enter a restricted mode:

| Action           | Allowed in Plan Mode |
| ---------------- | -------------------- |
| Read files       | Yes                  |
| Explore codebase | Yes                  |
| Analyze code     | Yes                  |
| Edit files       | No                   |
| Run commands     | No                   |
| Execute tests    | No                   |

The agent explores your repo, asks clarifying questions, and outputs a step-by-step plan. Once you're happy with the plan, you exit plan mode and let the agent execute it.

**I use plan mode for almost everything** - even small bug fixes. The crucial thing is that it validates my assumptions and helps me iterate toward a correct solution before committing anything to code.

## The Plan Mode Coding Loop

The loop is simple:

1. Dictate what you want. Can be high-level ("add user auth") or specific ("refactor `handleSubmit` in `LoginForm.tsx`").
2. Enter plan mode.
3. Iterate until the agent produces a plan you're happy with.
4. Exit plan mode and let the agent execute.

For large features, you might spend an hour in plan mode before writing any code.

You usually don't clear the context window between planning and execution. This means that when the agent starts executing, it already has all the relevant files and context from the planning phase. This is why plan mode works - it's not just about the plan document, it's about priming the agent's context.

The exception is multi-phase plans, where you break large features into separate planning/execution cycles. That's outside the scope of this article, but worth exploring once you're comfortable with the basic loop.

## ALWAYS Use Dictation

**If you're not using dictation with AI, you're falling behind**. Dictation lets you spit out ideas faster than any other input method.

I use [Wispr Flow](https://wisprflow.ai/) on Windows. [Superwhisper](https://superwhisper.com/) is great on Mac.

The key insight: AI doesn't need grammatically perfect input. Especially in plan mode - the agent rewrites your prompt anyway. So messy, stream-of-consciousness dictation works fine. The grammatically incorrect inputs at the top of the conversation history don't matter once the agent has refined them into a plan.

## How Plan Mode Helps The Agent

An agent can only work with what's in its context window. If it hasn't read a file, it can't edit it well, and if it doesn't understand your project structure, it'll make bad assumptions about where things belong.

Plan mode **builds that context window before any code gets written**. The agent explores your codebase, reads the files it'll need to modify, and discovers how different parts connect. By the time you exit plan mode, the agent has already loaded everything it needs.

The plan document matters too. It gives the agent a clear set of instructions to follow during execution, rather than figuring things out as it goes. Between the loaded files and the explicit steps, you've eliminated a ton of failure modes. Code quality goes up significantly when the agent knows exactly what it's working with and what it needs to do.

## How Plan Mode Helps The Dev

You don't know what you want until you see it. This is true for clients, and it's true for you too. Don't fool yourself that you have perfect clarity before you start. You don't.

**Plan mode lets you prototype before touching the code**. You iterate with the agent on what you're building - discussing tradeoffs, validating assumptions, catching edge cases - all before a single line of code exists. This is the same process you'd go through with a colleague, except faster.

Plan mode is a forcing function for concrete requirements. You wouldn't chuck vague requirements at a human colleague and expect good results. Without plan mode, that's exactly what you're doing to an AI. Anyone who's maintained an open source repo and found themselves peering at a grubby screenshot of an error message knows what I'm talking about.

Plan mode makes you articulate what you want clearly enough that someone else can implement it. And often, explaining what you want reveals that you wanted something slightly different.

## How To Prompt Better In Plan Mode

You can customize how Claude Code behaves via an [AGENTS.md](https://agents.md) file in your project root. These tips help make plan mode more effective.

### Make Your Plans Concise

Plans shouldn't be novels. Tell the agent to sacrifice grammar for brevity. This makes plans scannable and keeps the focus on what matters.

```markdown
When writing plans, be extremely concise. Sacrifice grammar for the sake of concision.
```

### Make The Planner Ask Clarifying Questions

The agent will ask some questions by default, but you can make it more thorough. This catches ambiguities before they become bugs.

```markdown
At the end of each plan, list unresolved questions. Ask about edge cases, error handling, and unclear requirements before proceeding.
```

### Put The Summary At The End

In a terminal, you read the end of the output first. Tell the agent to put the actionable summary last so you don't have to scroll up.

```markdown
End every plan with a numbered list of concrete steps. This should be the last thing visible in the terminal.
```

## Isn't This Slower Than Doing It Myself?

Sometimes, yes. If you know a repo inside-out and can see the solution instantly, you'll probably be faster without the AI.

But plan mode isn't just about speed on familiar ground. It extends your reach. When you're in an unfamiliar codebase, or you need to think through requirements before diving in, plan mode is essential. It lets you contribute in places you couldn't before.

**I use plan mode for everything, even when I'm confident I could code it faster myself**. Three reasons:

1. **These tools keep improving.** Speed is one of the main areas they're getting better at. Every time I use plan mode, I build intuition about what AI can handle and how to communicate requirements to it. That skill compounds.

2. **Less mental fatigue.** Focusing on high-level decisions uses fewer brain cycles than fixing syntax errors and chasing type mismatches. I get more done with less exhaustion.

3. **AI is the best rubber duck I've ever had.** It understands codebases instantly and is available 24/7. Plan mode forces me to articulate what I want, which makes me better at building software. Both my code quality and output have gone up since I started using it.

The question isn't "is this slower right now?" It's "what am I optimizing for?" If you're optimizing for learning, reduced fatigue, and long-term effectiveness, plan mode wins even when you could technically code faster alone.

## Conclusion

Plan mode isn't optional. It's a foundational tool for AI-assisted coding.

1. **Use plan mode for everything**, even small bug fixes
2. **Use dictation** - AI doesn't need perfect grammar
3. **Configure AGENTS.md** to make plans concise with questions at the end
4. **Planning helps the agent** by building its context window before it codes
5. **Planning helps you** by forcing you to articulate your requirements
6. **It might not always be faster right now**, but it's a long-term investment in your skills

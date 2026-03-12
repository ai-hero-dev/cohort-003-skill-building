A: So at this point in the course I'm basically introducing different human-in-the-loop patterns for how you can introduce the human back after we've worked on so much AFK work. I think an important part of that is designing software architecture. I want to give people a flavor for what good software architecture looks like and why it's important for AI. The theory here is that without good software architecture the AI is totally; it goes in essentially as a new starter because it's completely stateless and it doesn't, by itself, gain memory of the codebase. A difficult software architecture will make the codebase really hard to navigate for AI. I think what I want to give people is some language they can use to talk to the AI about what good software architecture should look like. They should maintain throughout that planning phase and during the implementation phase a sense for what the architecture is. I think that obviously this could just grow and grow and grow but I think what I want to nail down with you is the exact terms that I should teach them. I think the idea of teaching interfaces is a really important part of this because an interface means we can hide a lot of implementation complexity inside an interface. We also need to say that feedback loops link into this as well because if something has a simple interface but a complex implementation inside, that makes it really easy to test. For AI we basically need to structure the code so that the places that it can find these interfaces and understand the deep modules within the codebase are present in the file system.

Q: I'm hearing something really important here, but I need to push back on scope before we nail the teaching sequence.

Let me map where this sits: You're in **08-human-in-the-loop-patterns**, and the previous lessons (08.01-08.07) have been about *tasks* — what makes a task HITL vs AFK, kanban patterns, research, prototyping, QA. Those are all about *how you split work*. This lesson pivots to *how you structure code* to support that split work.

The **next lesson (08.09)** is about adding module awareness to the plan/PRD skill — which means this lesson needs to establish what "module awareness" even *means*.

Here's my read on what you're describing, and I think you've got **three separate lessons** compressed into one:

1. **Why AI needs clear interfaces** — the philosophical foundation (why interfaces are load-bearing)
2. **How to design for AI readability** — practical architecture patterns (cognitive load, discoverability in the filesystem)
3. **How to *talk to the AI* about architecture** — the language/framing you use in prompts and agents.md to keep architecture in focus

Those aren't the same lesson. The first is foundational. The second is tactical. The third is about translating the first two into agent steering.

**Before I ask you to choose:** what's the ONE thing you want learners to be able to do after this lesson that they can't do now? 

Is it:
- A) Understand why good architecture matters for AI (so they're motivated to care)?
- B) Recognize what makes a codebase "AI-friendly" vs "AI-hostile"?
- C) Actually *design* or *redesign* a codebase to be more AI-friendly?
- D) Talk to Claude Code (via agents.md or prompts) using the right vocabulary about architecture?

Because those are meaningfully different scopes, and the course structure tells me you probably can't do all four in one lesson.

A: I think A and B are what we want out of this lesson. Maybe C could be its own lesson and D we're kind of covering in the next lesson.

Q: Good. That's clearer. So this lesson is **foundational and diagnostic** — build intuition about *why* it matters and give them a lens to *recognize* good vs bad architecture for AI.

Now I need to understand the depth you're going for, because "interfaces" and "cognitive load" can go really shallow or really deep.

Let me ask three probing questions:

**1. On interfaces:** Are you talking about the *concept* of interfaces (things that hide complexity) or the *mechanics* (like actual TypeScript/Python interfaces, abstract classes, etc.)? I'm guessing the former — that you want them to understand "an interface is a contract that lets you hide nasty stuff inside" — but I want to be sure we're not sneaking implementation details in here.

**2. On cognitive load:** You mentioned "places that it can find these interfaces and understand the deep modules within the codebase are present in the file system." That sounds like you're talking about **filesystem structure as a readability signal**. Is the core insight: "If your files/folders tell a story about what the system does, Claude Code can navigate it faster"? Or is there more to it than that?

**3. On scope creep:** You mentioned DDD (Domain-Driven Design) in the course outline. Are you planning to teach DDD concepts here, or just borrowing the *language* of "domains/modules" as a way to talk about cognitive boundaries? Because if it's the former, this lesson balloons.

What would help me most: **Can you sketch out 3-4 concrete code examples** (ideally from the student's final repo or a simple variant) that show "AI-hostile" vs "AI-friendly" architecture? That would tell me exactly what level of detail you're targeting.

A: Yeah I guess we're talking about the concept of interfaces here. Yep that sounds right. On number two. I think it makes sense to give a nod to DDD and give people a link if they want to learn more but I definitely don't want to teach DDD.

So I would describe AI hostile architecture as one with essentially no facades. Everything is exposed. All functions are available to all other functions. What this means is that the AI needs to work through the entire dependency chain or massive chunks of it in order to find the relevant groups of information. Whereas if you break your system down into larger chunks, the AI reflects that in the file system and maybe even in some documentation, then the AI can really easily navigate that and understand the relationships a lot simpler.

Q: Perfect. Now I can see the shape of this.

So the core insight is: **AI navigates codebases the same way humans do — by following the filesystem structure and visible boundaries. Lack of facades forces the AI into cognitive overload because it has to hold too many relationships in context at once.**

That's clean. That's teachable in one lesson.

But I need to push back on one thing: you said "maybe even in some documentation" — I want to make sure we're not accidentally making this lesson about *how to document your code*. That's a different skill. This lesson is about **structure**, not documentation. The documentation is a side effect of good structure, not the thing itself.

So let me test my understanding with a concrete question:

**If you had to show one "before/after" example, would it be:**
- A monolithic file with 50 functions all calling each other, vs the same logic split into 3-4 modules with clear boundaries?
- A codebase where everything is in `src/` vs one organized as `src/auth/`, `src/payments/`, `src/ui/` etc?
- Something else entirely?

And here's the thing I'm really trying to nail: **How much actual code should be in this lesson?**

My instinct says: **keep code examples minimal and focused on *structure*, not implementation.** Show the before/after *shape* of a codebase, not 100 lines of function bodies. The point isn't "here's how to write X correctly" — it's "here's why AI struggles with Y shape and thrives with Z shape."

Does that match your intent, or do you want to show actual working examples?

A: Yeah I think this would be a knowledge-based lesson not a skills-based lesson.

Q: Excellent. That's the clarity I needed.

So this is **pure explainer** — no hands-on exercise, no "now you try." Just building the mental model and the vocabulary.

That actually lets me push the scope even tighter. Here's what that means:

**You can keep code examples purely illustrative.** Small snippets that show the *shape* of bad vs good, not production-ready examples. Think: enough code to see the problem, not enough to learn implementation patterns.

**You can be more aggressive about abstraction.** "Here's why all functions exposed in one file is bad" — diagram or tiny example. "Here's why modules with clear boundaries is good" — different diagram or tiny example. Move on.

**You don't need to prove these concepts work** — you're building taste/intuition, not teaching a technique they'll practice immediately.

Here's my last probing question before we lock scope: **How much should you lean into the "gray boxing" idea?** (I see it mentioned in the outline.) 

Is the takeaway: "The AI should understand the *public interface* of a module without needing to understand everything inside"? Because that's a really clean way to frame it — and it ties directly to why the *next* lesson (08.09, module awareness in the skill) matters. But I want to know if gray boxing is central to your argument or just a supporting detail.

A: Yeah I think this is the key or certainly part of the conclusion, which is that AI gives you the ability or rather having big chunks of implementation behind a testable interface allows you to not check the implementation that much because it means that the AI can kind of handle the stuff within that gray box. It's not a black box because you can look at it any time but it is a gray box because you don't necessarily need to know everything that's going on in there.

Q: Perfect. That's the keystone of the whole lesson.

So the argument structure is basically:

1. **The problem**: AI starts fresh each session, so it has to re-navigate the codebase dependency chain — unclear structure = cognitive overload
2. **The solution structure**: Break code into modules with clear public interfaces (facades)
3. **Why this works for AI**: The AI can treat each module as a "gray box" — understand the contract without holding all internal complexity in context
4. **The bonus**: Gray boxing also makes feedback loops better because you can test the interface independently

That's a complete, coherent lesson.

Now let me propose the teaching sequence and you tell me if it lands:

**Teaching Sequence:**
1. **Start with the problem** — Show an "AI-hostile" codebase (everything exposed, tangled dependencies). Why does this break AI? It has to hold the entire dependency chain in context.
2. **Introduce the solution: modules with clear boundaries** — What does good structure look like? Clear facade/interface per module. Show the filesystem shape.
3. **Connect it to context windows** — This isn't just philosophy. Limited context = limited ability to hold complexity. Good structure solves this.
4. **Name the pattern: gray boxing** — You can look inside when you need to, but you *don't have to*. This is the sweet spot for AI.
5. **Close with the multiplier effect** — Gray boxing also makes testing/feedback loops cleaner, which links back to Day 4 and forward to how you'll steer agents in 08.09.

Does that sequence feel right? Or would you rearrange anything?

A: I don't think it's really about context windows. It's more about how information is organized and how easy it is for AI to navigate that graph. If you think of a codebase as a kind of documentation site for itself, then you want to make sure that all of the parts of that site are well organized.

Q: Ah, that's important. You're not saying "the AI runs out of context so we need to organize code" — you're saying "the AI navigates the codebase like a graph, and a well-organized graph is easier to traverse."

That's actually a cleaner argument and it *doesn't* hinge on token limits. It's about **discoverability and navigation**, not resource constraints.

Let me revise the sequence:

**Teaching Sequence (revised):**
1. **Start with how AI navigates code** — The AI is reading your codebase like a graph. It starts somewhere and follows connections (imports, function calls, filesystem structure). The shape of that graph determines whether navigation is fast or slow.
2. **Show the problem: bad graph structure** — When everything is exposed and tangled, there are too many possible paths. The AI has to explore endlessly to understand what matters. (Show AI-hostile example.)
3. **Introduce the solution: modules with clear boundaries** — By grouping related code and exposing only a public interface, you *reduce the graph*. Fewer connections to follow means faster navigation.
4. **Name the pattern: gray boxing** — The interface is the contract. The AI understands the "what" without needing to hold all the "how" at once. It can zoom in when needed, but doesn't have to live inside the implementation.
5. **Close with the multiplier effect** — Clear boundaries also make testing/feedback loops cleaner. This ties back to Day 4 and sets up how agents will use this structure in 08.09.

Does that better capture what you mean? Does the sequence still work, or would you shuffle it?

A: Looks good.

Q: Excellent. Now one final check before we lock this down:

**In scope vs Out of scope** — I want to make sure we're crystal clear on boundaries:

**I'm assuming OUT of scope:**
- How to *actually refactor* a messy codebase into modules (that's lesson C, which could be its own thing)
- Specific architectural patterns (MVC, layered architecture, etc.) — we're just talking about the principle of boundaries
- Testing strategies in detail (Day 4 covered this; we're just noting the connection)
- How to write agents.md or prompt the AI about architecture (that's 08.09)
- Domain-Driven Design deep dive (just a nod and a link)

**I'm assuming IN scope:**
- What makes a codebase "AI-hostile" vs "AI-friendly"
- The mental model of a codebase as a graph/navigation problem
- The concept of facades/public interfaces
- Gray boxing as the key pattern
- Why this matters for AI specifically (not just general software engineering)

Does that match what you're building? Anything I've put in the wrong column?

A: Yep looks good.

Q: Perfect. Here's your **Scope Summary**:

---

**Scope Summary**

**Lesson title**: Designing Codebases AI Loves

**Core takeaway**: AI navigates codebases as a graph of relationships. Well-organized code with clear module boundaries and public interfaces makes that graph easy to traverse; tangled code forces the AI into endless exploration. You can design for this.

**Prerequisites**: 
- Understanding of Day 4 feedback loops (why testing matters)
- Familiarity with how Claude Code reads and navigates files (from 02-getting-to-know-claude-code)
- The concept of HITL vs AFK tasks (08.01-08.02)

**In scope**:
- What makes a codebase "AI-hostile" (tangled dependencies, everything exposed, no clear boundaries)
- What makes a codebase "AI-friendly" (modules with clear boundaries and public interfaces)
- How AI navigates codebases as a graph — why structure matters for traversal speed
- The concept of facades and public interfaces as load-bearing abstractions
- Gray boxing: understanding the contract without holding all implementation complexity
- Why this pattern matters specifically for AI (not just general software design taste)
- The connection to feedback loops and testing (references back to Day 4)

**Out of scope**:
- How to refactor an existing messy codebase (separate lesson)
- Specific architectural patterns (MVC, layered, etc.)
- Deep dive into Domain-Driven Design (mention with link for interested learners only)
- How to communicate architecture to agents via agents.md (08.09 covers this)
- Testing strategies in detail (Day 4 already covered)
- Actual code implementation examples beyond illustrative snippets

**Teaching sequence**:
1. **How AI navigates code** — Establish that a codebase is a graph of relationships (imports, calls, filesystem structure). The AI traverses this graph to understand what it needs to do. The shape of the graph determines navigation speed.
2. **The problem: AI-hostile architecture** — Show tangled, exposed code. What happens when everything is reachable from everything else? The AI has too many paths to follow and can't easily find what matters.
3. **The solution: modules with clear boundaries** — Introduce the concept of grouping related code and exposing only a public interface (facade). This *reduces the graph* — fewer connections to follow.
4. **Gray boxing: the key pattern** — Name it. The interface is the contract. The AI understands what the module does without needing to hold all internal complexity. It can zoom in when necessary, but doesn't have to live inside.
5. **The multiplier effect: feedback loops** — Clear boundaries also enable clean testing and feedback loops (connect back to Day 4). This sets up why module awareness in agents.md (08.09) is powerful.

---

You're ready to write. Keep code examples **small and illustrative** — show the shape of the problem and solution, not production code. This is about building taste, not teaching technique.
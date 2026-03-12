# Scoping Document: Designing Codebases AI Loves

## Scope
AI navigates codebases as a graph of relationships. Well-organized code with clear module boundaries and public interfaces makes that graph easy to traverse; tangled code forces the AI into endless exploration. You can design for this.

## Prerequisites
- Completion of Day 4 feedback loops section (why testing and clear interfaces matter)
- Familiarity with how Claude Code reads and navigates files (from 02-getting-to-know-claude-code)
- Understanding of HITL vs AFK task designation (08.01-08.02)
- Exposure to the concept of testable interfaces and feedback loops

## In Scope
- What makes a codebase "AI-hostile" (tangled dependencies, everything exposed, no clear boundaries)
- What makes a codebase "AI-friendly" (modules with clear boundaries and public interfaces)
- How AI navigates codebases as a graph and why structure matters for traversal speed
- The concept of facades and public interfaces as load-bearing abstractions
- Gray boxing: understanding a module's contract without holding all implementation complexity
- Why this pattern matters specifically for AI (not just general software design philosophy)
- The connection to feedback loops and why testable interfaces enable better AI behavior

## Out of Scope
- How to refactor an existing messy codebase into modules (separate future lesson)
- Specific architectural patterns (MVC, layered architecture, etc.)
- Domain-Driven Design deep dive (mention with context-appropriate link only)
- How to communicate architecture to agents via agents.md (covered in 08.09)
- Testing strategies in detail (Day 4 already covers this)
- Actual code implementation examples beyond small, illustrative snippets

## Teaching Sequence
1. **How AI navigates code as a graph** - Establish that a codebase is a network of relationships (imports, function calls, filesystem structure). AI traverses this graph to understand what needs doing. Shape of the graph determines navigation efficiency.
2. **The problem: AI-hostile architecture** - Show tangled, over-exposed code. What happens when everything is reachable from everything else? Too many possible paths, unclear what matters, AI wastes effort exploring irrelevant connections.
3. **The solution: modules with clear boundaries** - Introduce grouping related code and exposing only a public interface (facade). This reduces the graph itself, fewer connections to follow, clearer navigation path.
4. **Gray boxing: the key pattern** - Name and define it. The interface is the contract. AI understands what the module does without holding all internal complexity. Can zoom in when necessary, but doesn't need to live inside the implementation.
5. **The multiplier effect: feedback loops** - Clear boundaries enable clean testing and feedback loops (connect back to Day 4). This preparation sets up why module awareness in the plan/PRD skill (08.09) becomes powerful.

---
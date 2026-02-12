# The Constraints Of LLMs

To work effectively with LLMs, you need to understand their fundamental constraints. These aren't bugs to be fixed — they're inherent properties of how the technology works.

## Attention Relationship Scaling

There is a finite amount of attention that LLMs have access to. Each token has a relationship to every other token, meaning the number of attention relationships scales quadratically — n² for n tokens.

| Tokens (n) | Attention Relationships (n²) |
| ---------- | ---------------------------- |
| 1,000      | 1,000,000                    |
| 10,000     | 100,000,000                  |
| 100,000    | 10,000,000,000               |
| 1,000,000  | 1,000,000,000,000            |

Each attention relationship is stored as a score in a KV cache. But this is only for a _single_ attention head. Production models run many attention mechanisms simultaneously — a model might have 80 layers, each with 64 heads. At 100,000 tokens, each head needs 10 billion scores, all of which must be computed, stored, and referenced to produce the next token.

This is the core reason that **more tokens = worse performance**. The attention budget gets spread thinner across more relationships, making it harder for the model to focus on what matters.

Some research into sparse attention (sliding windows, dilated/strided patterns, learned sparsity) aims to reduce this cost, but most production models don't document their attention mechanisms.

## Smart Zone / Dumb Zone

The attention scaling problem has a practical consequence: the further you go into the context window, the dumber the LLM gets.

Dex Horthy describes this as the "dumb zone" — roughly the last 40% of the context window. Before that is the "smart zone."

This is also related to the "Lost in the Middle" problem ([paper](https://arxiv.org/pdf/2307.03172)): LLMs are worse at utilizing information placed in the middle of their context. Information at the beginning and end gets more attention. This may be influenced by training data patterns — many texts (news articles, etc.) place the most important information at the start and end.

The practical takeaway: **keep your context lean and front-loaded**. Think of the context window like a UI — if you overload it with too much information, the model gets confused, just like a user faced with too many buttons on a page.

## Hallucinations

LLMs are lossy semantic compressors. Like JPEG compresses images and MP3 compresses audio, LLMs compress _meaning_. And like all lossy compression, they produce artifacts when pushed too hard.

Every lossy compressor can only reconstruct patterns present in its training data. JPEG can't reconstruct detail that was thrown away. LLMs can't reconstruct logic they never learned.

### Taxonomy

Hallucinations fall into two categories:

**Factuality Hallucinations** — the model produces factually incorrect information:

- **Factual Contradiction**: States wrong facts (e.g., entity errors, relationship errors)
- **Factual Fabrication**: Invents nonexistent facts (e.g., unverifiable claims, overclaims)

**Faithfulness Hallucinations** — the model deviates from given instructions/context:

- **Instruction Inconsistency**: Ignores user instructions (e.g., answers a question instead of translating it)
- **Context Inconsistency**: Contradicts provided context (e.g., summarizes a document incorrectly despite having the correct text)
- **Logical Inconsistency**: Internal logic breaks down mid-reasoning (e.g., correct first step, then contradictory second step)

Logical and contextual inconsistencies _increase as context grows_, because the attention relationships become more diffuse.

### Practical Implication

When working with coding agents, if the LLM invents methods on a library that don't exist, consider whether relevant examples are in its context. With newer libraries, factual fabrication is much more likely if you don't include relevant information. Pointing the model to previous implementations tamps down factuality-based hallucinations.

## Statelessness

LLMs have no persistent memory between conversations. Each invocation starts with a blank slate — the only information available is what's in the current context window.

As described in Legacy Codebases And AI: "It forgets everything that it learned during its last run. It's essentially stateless." Human developers working on a codebase are _stateful_ — they accumulate tribal knowledge over time. LLMs cannot.

This means:

- Every conversation must re-establish context from scratch
- The model has no tribal knowledge about your codebase
- You need to explicitly provide relevant context each time (via system prompts, RAG, CLAUDE.md files, etc.)
- Tools like persistent TODO lists and structured notes help agents retain context across turns within a single conversation — but across conversations, it's gone

## Knowledge Cutoff Dates

LLM training data has a cutoff date. Anything that happened after that date is invisible to the model's parametric knowledge (the compressed knowledge baked into its weights).

Retrieved context (via RAG, tool use, etc.) is viewable in its complete, uncompressed form. But training data the model relies on is compressed into an incredibly small package — lossy compression of the entire internet into a set of model weights.

This distinction matters:

- For well-known, stable knowledge: the model's parametric knowledge is usually reliable
- For recent events, new libraries, or evolving APIs: you _must_ provide context via retrieval
- Older models could over-rely on parametric knowledge even when context contradicts it, though post-training techniques have improved this

The practical takeaway: **don't trust the model's built-in knowledge for anything time-sensitive**. Always provide up-to-date context for recent information.

# Scoping Document: The Constraints of LLMs

## Scope

Developers new to Claude Code need to understand the fundamental technical constraints that make LLMs behave differently from human colleagues — not to master the theory, but to build the right mental model for why the tool works the way it does.

## Prerequisites

- Basic familiarity with what Claude Code is (from course onboarding)
- No prior knowledge of transformer architecture, attention mechanisms, or LLM internals required

## In Scope

- **Context window as the core constraint**: Every token added creates O(n²) attention relationships, not linear growth
- **The smart zone vs. dumb zone**: Performance degrades predictably as context fills (~80k tokens on a 200k window is the danger zone)
- **Hallucinations as lossy compression**: LLMs are fuzzy compressors of world knowledge, forced to make up plausible answers when uncertain
- **Statelessness**: Zero memory between conversations; each reset is like onboarding a new developer to your codebase
- **Knowledge cutoff dates**: Training data has a hard end date; recent library versions/APIs are invisible to the model
- **Why these constraints matter**: Bad mental models lead to bad usage patterns, frustration, and blaming the tool instead of working with its constraints

## Out of Scope

- **Attention mechanism deep-dive**: No matrix math, no attention head visualization, no KV cache implementation details
- **How to manage these constraints**: Practical solutions (clearing context, system prompts, RAG, agents.md files) come in later lessons
- **Comparing different models**: This is about Claude specifically; differences with other LLMs not covered here
- **Fine-tuning or training**: Training process is not relevant to understanding operational constraints
- **Specific prompt engineering techniques**: Applied strategies belong in Day 2 (steering) and beyond

## Teaching Sequence

1. **Open with the mental model problem** — "Junior developer" analogy breaks down immediately; explain why LLMs are fundamentally stranger
2. **Attention scaling / smart zone first** — The football league analogy makes the O(n²) problem concrete without math; this unlocks why later constraints exist
3. **Hallucinations as compression artifacts** — Explain the JPEG metaphor (lossy compression of all world knowledge into model weights); connect to sycophancy (wanting to help so badly it bullshits)
4. **Statelessness and its codebase implications** — Frame as "every conversation is a new starter" and "Memento guy with tattoos"; this shifts responsibility back to code quality, not model capability
5. **Knowledge cutoff as the final compression problem** — Brief; ties back to lossy compression + another reason you can't use LLMs as databases
6. **Land the main insight** — These aren't bugs to fix; they're constraints to design around. That's why the rest of the course exists.

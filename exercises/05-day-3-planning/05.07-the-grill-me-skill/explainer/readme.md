Throughout the process of recording this cohort, I've started to take the skills that previously were big skills that did multiple things and decompose them into smaller skills which just do one thing really, really well.

For instance, here in step three, it says "interview the user relentlessly about every aspect of this plan until you reach a shared understanding. Walk down each branch of the design tree, resolving dependencies between decisions one by one."

![Step three of a plan showing interview requirements](https://res.cloudinary.com/total-typescript/image/upload/v1774864929/ai-hero-images/b7tpprsgb45tgrbptsbv.png)

What I noticed is that sometimes I just wanted this bit without the rest of the behavior. I didn't actually want to create a PRD, I just wanted to be grilled by the LLM.

So I took this skill and put it inside its own skill here and added a couple of bits here.

```markdown
---
name: grill-me
description: Interview the user relentlessly about a plan or design until reaching shared understanding, resolving each branch of the decision tree. Use when user wants to stress-test a plan, get grilled on their design, or mentions "grill me".
---

Interview me relentlessly about every aspect of this plan until we reach a shared understanding. Walk down each branch of the design tree, resolving dependencies between decisions one-by-one. For each question, provide your recommended answer.

Ask the questions one at a time.

If a question can be answered by exploring the codebase, explore the codebase instead.
```

## Meet The `/grill-me` Skill

This is the `/grill-me` skill and it has been extremely useful in all sorts of different contexts, not just coding.

What I've started doing is actually having a grilling session before I then go to the PRD. And this grilling session can often last, you know, like 40 or 50 questions long or something. It can be really intense.

But I've also started using this outside of coding too. So I'll just get the LLM to grill me about ideas so we reach a shared understanding, reach the shared idea of what we're trying to build or trying to do, and only then will I allow it to implement.

I found it to be a very powerful version of plan mode, but again, without the directive to create an asset at the end.

## When To Use `/grill-me`

So when should you use this? What should your mental model be for using `/grill-me`?

You should use it anywhere that you have a vague concept that you want to be hardened into something that the LLM can actually produce.

You can do a grilling session based on just a couple of sentences, or just based on a very vague idea, similar to what we've been doing already. Then it will ask you questions just one at a time until you end up with something that looks like a stronger plan.

| Use Case              | Description                                                |
| --------------------- | ---------------------------------------------------------- |
| Pre-PRD Planning      | Flesh out vague ideas before creating a formal PRD         |
| Design Review         | Get grilled on your design decisions to catch issues early |
| Concept Validation    | Harden a vague concept into something implementable        |
| Cross-Domain Planning | Works for coding, writing, product design, and more        |

It will really help you both kind of flesh out the idea and then flush out any uncertainty. Or at least flush out the uncertainties that can be flushed out at that point, because sometimes you just need to get into code.

## Getting Started With `/grill-me`

You can add the `/grill-me` skill to your own repository using the following command:

```bash
npx skills add mattpocock/skills/grill-me
```

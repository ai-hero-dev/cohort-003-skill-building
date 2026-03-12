So we've been talking about `AGENTS.md` and progressive disclosure, and we've not been very kind to `AGENTS.md`.

So wouldn't it be great if there was a built-in solution accepted by the community as the right way to do progressive disclosure when you're steering agents?

## Agent Skills

And that solution is [Agent Skills](https://agentskills.io/home). It's an open format accepted across coding agents, including Claude Code.

It is a simple open format for giving agents new capabilities and expertise.

Agent skills are folders of instructions, scripts, and resources that agents can discover. **The key word there is discover**, because they are not forced to take this information in. They're not forced to see it, but it is in a place that they can easily discover it.

## How Skills Work: Progressive Disclosure

Let's take our example from before to illustrate what we mean.

![Diagram 1](https://res.cloudinary.com/total-typescript/image/upload/v1773313271/ai-hero-images/ohrykvr4ete28rnzwdba.png)

Before, all of these React Router-style instructions were just forced on the agent. They were present in its context window. Same for all of these front end ones and same for all of these database ones. All of the instructions were right there.

But what if instead we refactored these into their own file and we gave a little bit of metadata to the agent to say: use this skill when you need help with the React Router Framework, use this one when you need help writing front-end code, use this one when you need help writing database or Drizzle code.

And so all the agent would see by default would be the name of the skill and then the description of the skill:

![diagram-3.png](https://res.cloudinary.com/total-typescript/image/upload/v1773313272/ai-hero-images/etzgdziosi53zajtjn2w.png)

And then if it chose to, inside the session, it could basically call the React Router skill and bam—all of the instructions would become available to it:

![diagram-4.png](https://res.cloudinary.com/total-typescript/image/upload/v1773313273/ai-hero-images/vupzrsa3oohlift9fdoc.png)

This is the idea behind skills: **they allow you to progressively disclose instructions**.

They also allow you to kind of build a user interface for your agent of all the information it might need to know.

## Skills in Practice

Inside the repo, I've added a couple of example skills. These are skills that I genuinely found were very useful while I was building out this application.

If we open up the Explorer, we can see them inside `.claude`, then `skills` here. And there are two skills here: one for a better SQLite 3 rebuild, and the first one we're going to look at is `pnpm-not-found`:

![Showing the position of skills in the explorer](https://res.cloudinary.com/total-typescript/image/upload/v1773313274/ai-hero-images/h9b2yp7tfykepyb1lm15.png)

Notice how these skills, just like the `CLAUDE.md`, are inside the project folder. Just like `CLAUDE.md`, you can have them inside the project like this, or you can have them scoped globally to your user.

In my setup I've got some user scoped skills and some local skills. Of course, the ones that are scoped to the project are much easier to share with your teammates as well. So that's worth thinking about too.

If we click into `SKILL.md` here, we can see that it follows a certain pattern. It has a piece of front matter at the top here, which has the name and the description.

```yaml
---
name: pnpm-not-found
description: Fix pnpm command not found errors by enabling corepack. Use this when pnpm cannot be found, corepack errors appear or the package manager is missing.
---
```

It turns out that LLMs really don't know about corepack, and maybe [you don't either](https://github.com/nodejs/corepack)! But if you encounter errors like `pnpm command not found`, you can just run `corepack enable` and then everything will wire itself together.

So this is a perfect thing to put in a skill because I don't want this in a global `CLAUDE.md` file because the error really only happens very rarely. But when it does happen, it's really high leverage for the LLM to know how to fix it.

## More Skill Examples

The other skill that I've got here is this `better-sqlite-3-rebuild`. The description reads:

![Use when seeing errors about better-sqlite3 native module...](https://res.cloudinary.com/total-typescript/image/upload/v1773313276/ai-hero-images/hdi4u1otawlbuukafo7r.png)

So it's a very clear description of when I wanted to invoke this skill. It's again, very similar to the other pnpm skill that we had there. It's just trying to fix a relatively rare issue where if it's a Node module version mismatch, then it should run `npm` or `pnpm rebuild`.

These are perfect use cases for skills because we're just steering the LLM in the right direction to avoid a rare issue.

## Progressive Disclosure Within Skills

Now you may be thinking: if you look at this diagram, how possible is it to go even further in the progressive disclosure?

Is it possible within the React Router skill to have other documents inside there that might speak to specific weirdnesses with React Router? Could you potentially take the entire React Router documentation and put it inside a skill?

Well, you absolutely could.

For instance, if you wanted to just create an extra little file inside `better-sqlite-rebuild`, perhaps just take this and just imagine this is like a more complex script than you think, put it inside `script.sh`, and then you can just have the script in there and reference it from this file.

The way you reference it is simply by using a markdown link here that's very, very easy for the LLM to follow.

![Showing how to use a markdown link](https://res.cloudinary.com/total-typescript/image/upload/v1773313279/ai-hero-images/lsnkouyoreezvg305cug.png)

So this is a great way of hiding complexity within your skill. Your skill might want to bundle scripts, it might even bundle images. You could bundle anything you can put on the file system inside a skill, but you don't have to put it inside the proper `SKILL.md` file.

## Two Types of Skills

I want to note something interesting finally, which is I think of there as being two types of skills.

| Skill Type        | Who Invokes? | Use Case                                                                                  |
| ----------------- | ------------ | ----------------------------------------------------------------------------------------- |
| **Agent-invoked** | The LLM      | Skills that help the agent complete its task (e.g., validation rules, framework guidance) |
| **User-invoked**  | The human    | Skills that change agent behavior (e.g., write a PRD, run TDD, plan a refactor)           |

Skills that you want the LLM to invoke, such as the ones that we've been looking at here, or skills that you personally want to invoke.

You can invoke a skill in the same way that you invoke any command inside Claude. We can actually use the `skills` command to list all the available skills.

```
/skills
```

You can see we've got some project skills here and I've got a bunch of user skills up here:

![Showing project and user skills](https://res.cloudinary.com/total-typescript/image/upload/v1773313281/ai-hero-images/sukbcfzlnuh5ihdbgo29.png)

And we can press escape to close this.

To invoke a skill, all we've got to do is just, let's say, use one of these skills here. So let's say we just invoke the `better-sqlite-rebuild` skill:

![Invoking the better-sqlite-rebuild skill](https://res.cloudinary.com/total-typescript/image/upload/v1773313282/ai-hero-images/ad6qomeiixh9snjaamck.png)

And I just pressed return here to invoke it.

## Agent-Invoked vs. User-Invoked

Now the difference between a user invoked skill or an LLM invoked skill is basically what you do with this description:

![Showing the description of the skill](https://res.cloudinary.com/total-typescript/image/upload/v1773313283/ai-hero-images/orzf1fsurpppysvlpvu0.png)

Because this description is a description to the agent to use this skill under certain conditions.

It turns out that if for whatever reason we didn't want to allow this skill to be used by the LLM, we can actually just omit the name and description here. This is kind of like in our diagram just deleting the metadata that gets included to the LLM:

![Showing a description deleted from the original diagram](https://res.cloudinary.com/total-typescript/image/upload/v1773313284/ai-hero-images/bqukqe8ax2igqc64xyxz.png)

Now this React Router skill would only be invocable by the user. The LLM would have no reason to invoke it because it can't see a reason for doing so. There's no description of "use when."

So I find user invoke skills a really cool mechanism for steering the LLM to my preferences without needing to add an extra instruction like a description to the context window.

## Summary

So that's what agent skills are. They are a mechanism for steering the LLM using progressive disclosure.

And I think of there as being two groups: either user invoked skills or LLM invoked skills.

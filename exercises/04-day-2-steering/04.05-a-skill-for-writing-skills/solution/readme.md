Let's run our `/write-a-skill` skill and see what we get. As we can see, it's gone into a research mode where it's going to research Valibot's API and examine the Zod usage patterns in this repo in parallel.

So it's kicked off a task here where it's going to do a bunch of different web searches:

![Claude Code doing Web Searches](https://res.cloudinary.com/total-typescript/image/upload/v1773314220/ai-hero-images/rkgrprmp8zphmphnarr2.png)

It's then requesting to find individual pages here. This one looked particularly high value. "Migrate from Zod" — yes, I think we'll definitely need that.

## Exploring the repository

Okay, it has now decided to make the skill directory. It is creating it within `.claude/skills/zod-to-valibot`. And it is kicking out a pretty big file here, which I'm just going to accept unseen for now until we get in there.

So where is it? Aha, I'm actually going to interrupt it because it's actually put it inside my project Claude directory. I actually want it local to this project:

![Telling Claude I want it to be local to the project](https://res.cloudinary.com/total-typescript/image/upload/v1773314221/ai-hero-images/hokjqjwohonkhhwlullk.png)

So it's now asking to run a command which is going to move it, so yes that's fine. And it's going to create some extra files here for what looks like progressive disclosure, that's nice:

![Showing a REFERENCE and EXAMPLES.md file](https://res.cloudinary.com/total-typescript/image/upload/v1773314222/ai-hero-images/qducuwkqzbsmbwvtjiqr.png)

## Examining the generated skill

While that's going on, let's take a look at it. This is the Zod to Valibot file.

First of all, we can see the name and the metadata are up here:

![Showing the skill](https://res.cloudinary.com/total-typescript/image/upload/v1773314223/ai-hero-images/rzcdpthdzrxxdd46etdm.png)

It says "migrate TypeScript code bases from Zod to Valibot". The description reads:

> Use when the user mentions Valibot, wants to replace Zod, migrate validation schemas, or reduce bundle size with tree-shakeable validation.

Now this description reads to me like it's a skill that the LLM is supposed to invoke and it's giving the LLM rules for when it should invoke it. For me, I think of this as a user invoked skill. So I don't see a reason to provide a description here because we never really want the LLM to use it itself. It's a command that we always run. So I'll delete the frontmatter there:

![Skill without frontmatter](https://res.cloudinary.com/total-typescript/image/upload/v1773314224/ai-hero-images/xl606lkfpofby7zfy94p.png)

## Step-by-step migration guide

The skill comes down with a clear step-by-step guide:

- Install Valibot: `npm install valibot`
- Try the automated code mod first
- Review the output for errors
- Fix whatever the code mod missed
- Use this progressively disclosed `REFERENCE.md` file
- Migrate any validation wrappers
- Update all of the imports
- Verify by running the type checker
- Run the tests
- Remove Zod from dependencies

And then it's got a list of critical gotchas. That's so cool.

Let's take a quick look inside `REFERENCE.md`:

![A very complete-looking API reference for Zod to Valibot](https://res.cloudinary.com/total-typescript/image/upload/v1773314225/ai-hero-images/z5jagqxsolvya9mrvzxw.png)

And we can see this looks like a really complete API reference. This is again a benefit of progressive disclosure here because we can just stick all of this stuff in and it won't be seen until it's needed.

We could even probably progressively disclose this further by putting more of these groupings into further files referenced from here, kind of like a traditional documentation site.

Let's also look at `EXAMPLES.md` here:

![A very in-depth-looking set of examples for moving from Zod to Valibot](https://res.cloudinary.com/total-typescript/image/upload/v1773314227/ai-hero-images/h5tluf06mekn4fsnes5y.png)

So very nice. Just a whole load of different examples that go from Zod to Valibot.

## Invoking the new skill

Okay, let's try running this now. I'm going to cancel out of this. I'm going to run Claude again, and I'm just simply going to run:

```
/zod-to-valibot
```

OK, so it wants to install Valibot, which is a good start. I'm not feeling the need to particularly babysit this here. I'm fairly happy just to let it run:

![Claude running the Valibot migration](https://res.cloudinary.com/total-typescript/image/upload/v1773314228/ai-hero-images/c9p4li99098krbla7db3.png)

And just in anticipation, I'm going to turn on "Accept Edit On" using Shift-Tab to make sure that all of the edits are going to work.

## Monitoring context window usage

Oh dear, I have some concerns about our context window usage here. We are creeping up to 60%:

![Context window meter showing 60.6%](https://res.cloudinary.com/total-typescript/image/upload/v1773314229/ai-hero-images/reyejkmicl3teqe6vkji.png)

I'm hopeful that because the changes are relatively simple, we won't need to be too scared here. I.e. we can have some time in the dumb zone, but because the work is so simple, we don't necessarily need to be too scared. We can even see it's actually using some sub-agents here.

So it's actually running three task agents at once to migrate a bunch of stuff at once:

![Three subagents running at once](https://res.cloudinary.com/total-typescript/image/upload/v1773314230/ai-hero-images/ik4zmijtxj924sadixq7.png)

I'm a bit scared too that it's doing all of this stuff without referencing the feedback loops at all. It hasn't run any types or tests yet.

Certainly if I were doing this as a human developer, I would want to migrate a bit, then run the types and tests, and then migrate another bit, and that kind of thing. So this whole one big chunk thing was maybe a bad idea.

## Completing the migration

OK, all 19 root files migrated. Now it's asking to remove Zod, which I'm fine with:

![Claude requesting to remove Zod](https://res.cloudinary.com/total-typescript/image/upload/v1773314231/ai-hero-images/ggudgqqx3x8qlqtcysik.png)

And it's now running the type checker on this too, and it looks like there's an error:

![TypeScript error](https://res.cloudinary.com/total-typescript/image/upload/v1773314232/ai-hero-images/bfypxqbvzwdbixk37bkj.png)

This is where I start to get really worried about the context window because if there's any debugging to do or any fixing here, we are at 67% already and that is very scary. That's when I'm anticipating seeing some hallucinations creep in.

So at this point, I'm really watching the AI like a hawk to make sure that the code it's producing is okay.

OK, phew, it ran `tsc` again and there was no output, meaning that the type checking is passing. So now it's asking to run the test suite. Let's give that a go.

Alright, sweet relief, the 288 tests pass and the type checker is clean:

![Clean CI](https://res.cloudinary.com/total-typescript/image/upload/v1773314233/ai-hero-images/qz1g2tjgckrckmipz6zv.png)

## Reviewing the changes

Here we can see a simple schema here with `z.object`. Let's actually just go into the file so we can see what's changed:

![Diff of a Zod to Valibot change](https://res.cloudinary.com/total-typescript/image/upload/v1773314233/ai-hero-images/febners61esvfumzxoef.png)

We changed `z.object` into `v.object` with `v.pipe`, `v.string` and `v.minLength`. We have a discriminated union here which has been transformed into a `v.variant`:

![Discriminated union changed into `v.variant`](https://res.cloudinary.com/total-typescript/image/upload/v1773314234/ai-hero-images/ilcyh3ibeydu8pt5o2w9.png)

I would not have known how to migrate that personally, so it's pretty amazing that the skill knew how to do it.

If you know Valibot like I do, then you can go through some of the files like I just did and look at them and just sort of sense check them, make sure they look okay.

Otherwise, I'm going to do a little bit of QA on the site to make sure things are working fine.

You can feel free to QA a bit more in depth than I have, but this looks okay to me, especially since the types and the tests are both passing.

## The power of reusable skills

So just like that, not only have we migrated our entire repo, we've got a reusable skill that we can take and apply to any of the other repos in our setup.

This is, of course, just one use case for skills. They are just incredibly powerful for powering up our AI and then steering it in ways that match our preferences better.

We've seen both skills that I've used to help it recover from errors and now a user invoked skill where we can just transform its behavior and make it do a certain sequence of moves.

And of course, feel free to use the `/write-a-skill` skill to write some skills of your own. Nice work and I'll see you in the next one.

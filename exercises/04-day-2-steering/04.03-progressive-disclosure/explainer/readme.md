I've taken the CLAUDE.md file that we had in the last lesson and I have opened it out a little bit more and added a bunch of sediment inside here - as if a bunch of developers had gone in and added their own ideas into this file.

- [ ] Take a look at the file locally to see yourself.

![CLAUDE.md file with lots of lines in](https://res.cloudinary.com/total-typescript/image/upload/v1773311149/ai-hero-images/ymgwbyzxmigafms7fmeu.png)

If you've been using Claude with a bunch of teammates, then you probably have one that looks a little bit like this.

## Why This Is a Problem

Now this is not exactly ideal for reasons that we've already touched on. We have put a bunch of instructions into the global scope and not all of these are going to be relevant for every single request that we make of the LLM.

All of these instructions are going to be competing with the instructions that we give it in the prompt, for instance, in the plan.

![A bad instruction about positional parameters](https://res.cloudinary.com/total-typescript/image/upload/v1773311150/ai-hero-images/xenbetkcdb5j35205yli.png)

And if we're only touching front-end code that maybe doesn't have any positional parameters, that doesn't touch any services, maybe we don't even need to do any importing. Maybe we don't need to add a new ID to the database. Maybe we don't need to add a new timestamp to the database.

You know, all of these instructions are actually pretty narrow in the kinds of sessions that are going to need them.

## Visualizing the Context Window

I want you to imagine that each one of the instructions in the CLAUDE.md is one of these grey blobs in the context window.

![Diagram 1](https://res.cloudinary.com/total-typescript/image/upload/v1773311151/ai-hero-images/cttbjb3wafjcgpa2klz7.png)

Now it might be that only these little blobs here are actually relevant to front-end code. It might be that only these instructions are relevant for database code. Maybe these instructions are the ones that are relevant for React Router.

Now looking at all of these blobs, isn't it funny that we've got them grouped all into one file?

## The Solution: Organize by Relevance

Wouldn't it make more sense if they were grouped together?

Since a session that needs one piece of React framework advice will probably need more React Router framework advice.

So what if we group them like this instead where each one was in a separate file all located together and all of the unique ones were in their own file?

![Diagram 2](https://res.cloudinary.com/total-typescript/image/upload/v1773311152/ai-hero-images/jqjj0loe385oxtnir0ka.png)

And then inside the CLAUDE.md file you would have just a set of links which linked you to the correct grouping when needed.

So these would simply be separate markdown files and CLAUDE.md would use markdown links to link you to the right place.

## Introducing Progressive Disclosure

Now what we're organically discovering here is a really important concept that's going to recur throughout the rest of this course.

And that idea is progressive disclosure.

Progressive Disclosure is actually an idea that comes from UI and UX design. The idea is that bad UI involves putting all available actions into one huge screen that the user can scroll through and choose from.

If you've ever seen a menu of a bad website where it literally just has a hundred options up at the top in one single flat list, you know what I mean.

Instead, you should reduce the number of choices that the user has to make upfront and then allow them to find kind of information based on that small number of choices.

So Progressive Disclosure of Complexity is the name of the game. Instead of throwing all the complexity out at once, you just sort of give them a map and you allow them to navigate through it.

## Applying Progressive Disclosure

This CLAUDE.md file chucks all the complexity in at once.

And as this grows bigger and bigger, I would be much more likely to progressively disclose parts of it. In other words, take it from the CLAUDE.md, put it in separate files that aren't immediately visible to the LLM, and then just link it from the information that it does have inside CLAUDE.md.

![Looking at the CLAUDE.md again](https://res.cloudinary.com/total-typescript/image/upload/v1773311153/ai-hero-images/tymqbceex0svyik2zogh.png)

Now this concept of progressive disclosure is going to come up again and again and again throughout this course. It goes into software architecture and code-based design and all that stuff.

But in the next couple of sessions, we're going to look at this in the context of steering.

So, nice work and I will see you in the next one.

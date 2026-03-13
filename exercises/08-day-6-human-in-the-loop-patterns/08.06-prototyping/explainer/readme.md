Whenever you're embarking on a big build of something, especially something that doesn't have a precedent in the codebase, it's often extremely useful to get in an early prototype. This is a technique that software developers have been following for decades.

You're not quite sure what the client meant, so you provide them with a prototype they can play with, they can mess about with, and give you feedback on.

If you think of the plan mode as you and the AI trying to work out in-text what you're trying to build, prototyping allows you to actually make it concrete. And along with research, prototyping is a really key part of building good applications because you as the human get to impose your taste on the AI before it then goes into the Ralph loop.

### Where Prototyping Shines

**Front-end design**

I tend to use prototyping a lot for front-end design. I tend to get it to create multiple options for me on a throwaway route. This also means that when the Ralph loop goes and actually implements this, it's got this prototype to reference.

**Testing new tools**

This is also really great for testing new tools. For instance, you might want to just spin up a new library or something, maybe even in a throwaway repo. You want the LLM to really put the new library through its paces and test something out. Then having that janky little prototype that you can then feed into the actual implementation again is really great.

**Testing new services**

Research and prototype can work really well together. You research a bunch of possible options and then maybe you create prototypes for all of those options. Then you as the human can QA the prototypes, offer feedback, maybe iterate on them a little bit.

You end up with the best possible solution that can feed into a PRD and then break down into issues for the Ralph loop.

**What we're trying to do here is flush out the unknown unknowns really early on in the process.**

![Testing new services with prototypes](https://res.cloudinary.com/total-typescript/image/upload/v1773387316/ai-hero-images/bwta3wnsk6hbskqzlvge.png)

However, there are lots of places where prototyping isn't so useful:

| Scenario                        | Why It Works                            | Why It Doesn't                                                                                             |
| ------------------------------- | --------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| **Bug fixing**                  | We know what the desired behaviour is   | We just aren't meeting that behaviour                                                                      |
| **Extending existing features** | You're composing existing functionality | No need to prototype what a new modal might look like when you've already got a hundred in the application |

## How to Create a Prototype

For me, I don't tend to use a prototyping skill to create this prototype. I'll probably just invoke my `/do-work` skill and do a normal kind of human in the loop run with this.

The reason is I want to be close to the prototype, I want to be offering advice and applying my taste.

Once that's done, you can create the PRD leaning on information in the prototype. Then create the Kanban board too, again referencing the prototype locally.

![Approach to creating prototypes with Claude Code](https://res.cloudinary.com/total-typescript/image/upload/v1773387317/ai-hero-images/pdiyp9lkixer124qlz4y.png)

So this is really like a form of research, but instead of researching external stuff and saving explore phases, you're actually making the implementation step simpler.

And you cannot recommend it enough as an approach.

Prototyping, even before the PRD, or as part of building the PRD, is essential to applying your taste to products. It's great for design, it's great for testing out services, even great for software architecture.

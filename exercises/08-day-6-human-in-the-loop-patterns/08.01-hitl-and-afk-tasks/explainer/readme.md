Now that we've fairly successfully set up an autonomous agent to do our work for us, you might be thinking: can it do all of my work?

But surely it can't do all of my work, right? There are probably some things that require human in the loop involvement.

Your instinct is absolutely correct. When you're planning out work to complete a feature, you should be thinking carefully about which bits require human in the loop involvement, in other words, where you need to be present, and which bits can be done autonomously.

The dream is that we're able to delegate all of our work and don't need to be there for any of it. But the truth is that lots of work requires human in the loop involvement.

## What Needs Human In the Loop?

We already know one of the things that requires human in the loop: **planning**.

An AI can assist with creating a plan, but without the human, it doesn't have the source of truth to bounce off for what it's supposed to be creating.

Another thing we've seen in the course is **QA** (quality assurance). You need a human eventually to actually go in and test the thing that's being built.

Humans can surface things which aren't present in the AI's feedback loops:

- Does it feel good to use?
- Is it fast enough?
- Does it actually serve the purpose that I built this thing for?

## The Role of Taste

You might be getting a sense for the things that require human involvement. Anywhere that you need to apply **taste** to what you're doing.

What do I mean by taste? I mean human judgment, human feel.

| Area            | Why Humans Are Needed                         |
| --------------- | --------------------------------------------- |
| Planning        | Make design choices that feel sensible        |
| QA              | Give feedback based on personal taste         |
| Architecture    | Ensure the internal structure reflects values |
| User Experience | Ensure it feels right to end users            |

We need taste in planning because we need to work out together what we're building and make design choices that feel sensible.

We need QA because we need to look at the artifact that's created and give feedback based on our own tastes.

To create great products, we need to let humans and AI do the things that they're best at:

![Discussion of applying taste to development work](https://res.cloudinary.com/total-typescript/image/upload/v1773384598/ai-hero-images/egvwqhtdliiqiqgi8lp6.png)

## The Division of Labor

**The human should be there to:**

- Give their taste
- Give their opinion
- Give the feel to the application
- Shape how it performs externally to users
- Influence how it's built internally in its architecture

**The AI should be there to:**

- Pick up the grunt work
- Apply the human's taste to the canvas of the application code

If you delegate 100% to the AI, you're going to end up with a tasteless application, and often just something that plain doesn't work.

Throughout this section, we're going to be looking at ways that we can bring the human back in the loop in a productive way.

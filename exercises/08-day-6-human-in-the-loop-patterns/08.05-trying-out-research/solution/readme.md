All right, let's give this a go and see how it does.

We have our traditional explore phase as it goes and explores the project tech stack. It's now found that we have React Router v7, we have a full stack SSR, and crucially we have no existing real-time infrastructure.

![Claude Code exploring the project tech stack and findings](https://res.cloudinary.com/total-typescript/image/upload/v1773386983/ai-hero-images/x1wi9r5nb1rvwhvfuagg.png)

## Defining Your Constraints

Now here is where we get to apply our taste. You'll notice questions like scale expectations and fidelity versus simplicity, what should the UI show? We're really in kind of writing PRD territory and kind of grilling about expectations:

![Claude Code asking questions about scale expectations and UI requirements](https://res.cloudinary.com/total-typescript/image/upload/v1773386984/ai-hero-images/l3rchveegmf5sfwnkhk6.png)

In terms of scale expectations, imagine something like 20 students viewing the same lesson is probably realistic.

Here are the key constraints we're setting:

| Constraint             | Decision                                |
| ---------------------- | --------------------------------------- |
| Real-time capability   | True real-time                          |
| UI display             | Matt, Sarah, and two others are here    |
| Cursor/scroll tracking | Not needed                              |
| Service preference     | Third-party preferred over self-hosting |
| Data persistence       | Ephemeral (no storage needed)           |
| Unauthenticated users  | Don't count towards presence            |

The UI should show Matt, Sarah, and two others are here. Cursor scroll position is overkill. You're definitely open to adding a third-party service, and would probably prefer that to self-hosting it.

Presence data doesn't need to persist - it can be ephemeral. We don't need to worry about unauthenticated users counting towards presence.

## Researching Options

Okay, let's ping this off and see what it does now.

For the first time during this course, Claude Code has gone and launched some background agents. Those agents are researching Partykit, Pusher, Ably, and Liveblocks, and it's going to share its initial thinking on the tradeoffs of those.

![Background agents researching Partykit, Pusher, Ably, and Liveblocks](https://res.cloudinary.com/total-typescript/image/upload/v1773386984/ai-hero-images/kxvq8nl47b6tpldbmkwy.png)

You might not know about all of these, but that's the point of research. While you've been waiting, it looks like the agents have completed.

Super Bass Realtime and Live Blocks don't look right. Then we've got Pusher, Ably, and Party Kit. It looks like it thinks Ably is the best, and also has a super generous free tier, which is what you probably care about most in a toy application.

## Making Your Decision

Now you're going to answer its last few questions here. You agree that Ably looks really nice. You think you would prefer a managed API key service. You're comfortable with that `api.pusherauth.ts` idea.

And this is probably the most important one - let's make Ably the recommended approach for the research document.

So with that, you feel comfortable running it and we can get it to work.

![Claude Code kicking off the agent again to research Ably in depth](https://res.cloudinary.com/total-typescript/image/upload/v1773386986/ai-hero-images/cyi11dzmqhmy6uad3ucn.png)

It's now kicking off the agent again to research Ably again. This is a really nice in-depth exploration that we're able to do without using skills actually.

## The Research Document

Okay, it's come back from its final explore phase and it's written a markdown file for us.

This is that live presence indicator in the plans. And just take a quick look at the length there. We're talking a decent, hefty, nearly 300 line file.

![The generated research document showing top-level structure](https://res.cloudinary.com/total-typescript/image/upload/v1773386986/ai-hero-images/yqtocwrun8z5o4af3gg0.png)

Let's take just a quick look at the top and see what the top level items are:

- Requirements
- Recommended approach
- Implementation design
- Integration points in the existing codebase
- Alternatives considered

We might not need the alternatives section, but then it might be useful as a kind of architectural decision record. It's useful context for us to decide why we picked Ably.

So this then is the asset that would go into the PRD and go into any planning that we then go on to do from here. We've even still got just 18% context used here, so we could just go and write a PRD from this point too, directly from the research.

All of the issues in the Kanban board and everything would rely on this research.

## The Human In The Loop

I hope you can see now from having done it that the human in the loop part is really important.

What you would do for a production application is go into each service, kind of investigate in depth and verify what Claude was saying to you too. Because as part of research you often need to winnow down and figure out exactly what approach you want to take, or at least which one you want to prioritize now and maybe test out and prototype.

I'd love to hear [in the Discord](https://aihero.dev/discord) if you noticed anything different from that or if you have any great ideas for how you want to use research in the future. It's a really, really great tool. You don't use it every single time, but when you do, it feels really effective.

## File Organization and Documentation Decay

Suppose the last thing you should mention is why we're including it in the local file system instead of on like a GitHub issue.

The reason is that you want this to be really easily discoverable by Claude Code that's doing the implementing. You can certainly reference this file directly in the PRD and in the issues so it knows to go and read it. But if you later come back and you need to fix some bugs with the approach, then having the original research in the repo is going to be really useful.

However, as mentioned before, beware of documentation decay. If you eventually move away from Ably, or Ably changes their underlying SDK, then this research is going to go totally out of date and it's actively going to harm the agent working on this codebase instead of help it.

You tend to be really aggressive in deleting the stuff because you can always just check in the git history and pull it out if you need it.

Once you finish the implementation loop that's working on this feature, and once you finish the QA, then you can just delete it from the repo.

# Executing Our Multi-Phase Plan

## Running Phase 1

Let's run the implementation. I'm assuming it's going to do an explore phase.

Yep, there it is - as soon as I mention it, there it goes exploring. I'll check back in with you once it's complete.

![Claude Code terminal showing exploration in progress](https://res.cloudinary.com/total-typescript/image/upload/v1773322415/ai-hero-images/xsuw14qh0l96r6bzv26l.png)

All right, it has now completed the explore phase. It did that fairly quickly, took about a minute, and it's created a bunch of different tasks for itself:

![Showing different tasks](https://res.cloudinary.com/total-typescript/image/upload/v1773322416/ai-hero-images/uldczzvq5jbfis1sfz3t.png)

The first thing it's done is created the analytics service. Let me just give this a cursory review.

We are up here inside `analytics` service. Let's just check how big it made this and what it added to it.

Yeah, we can see here that it's really not providing that many analytics features:

![Relatively few analytics features in this file](https://res.cloudinary.com/total-typescript/image/upload/v1773322417/ai-hero-images/g9lzzogx5xydi8n0wy0w.png)

In other words, it's only put in here enough features to satisfy the tracer bullet. When we finish, this is probably going to be a pretty big file, but for now Claude is happy just to leave it small because we specified it should be a tracer bullet.

Fantastic. It's now running the tests too, which is good. So all 12 tests passed.

![Test output showing 12 tests passing](https://res.cloudinary.com/total-typescript/image/upload/v1773322418/ai-hero-images/kctneybzm2rscgkxudan.png)

Now it's going to build the UI component. With the previous plan, it would have spent a lot of time here building out the whole horizontal level, but we now have just enough signal to know that, okay, we're on target, we can proceed.

## Reviewing Phase 1

And now I can go in and actually QA this.

![Analytics dashboard UI showing summary cards and sparse data](https://res.cloudinary.com/total-typescript/image/upload/v1773322418/ai-hero-images/pkqcsek1vzggepvv4n1d.png)

So it's looking pretty nice, kind of pretty sparse.

We are getting some money shown up at 12 months. And if I hide my face here, we can see that if we switch to Sarah Chen, who's the other instructor, then we see other information here. So average rating is four, and she's got four enrollments, so that's looking great.

So notice how quickly we're able to gain confidence in what we're building by building this tracer bullet early.

Okay, I'm going to call that phase one complete. This is the decision that I was talking about. 34.3% is, well, I probably would definitely clear the context at 40%, right? And maybe definitely at like 35:

![34.4% Context Usage In Claude Code](https://res.cloudinary.com/total-typescript/image/upload/v1773322421/ai-hero-images/gqjxh9jmkxlzvmlppgha.png)

So I think I am going to clear the context here and free it up for a new phase.

## Moving to Phase 2

I'm then just going to press up a couple of times until I get to my prompt here for the plans on the PRD. I'm going to say instead of phase one, do phase two:

![Re-prompting](https://res.cloudinary.com/total-typescript/image/upload/v1773322429/ai-hero-images/piehpyf9l8iytdopiqqs.png)

Now, of course, then because we cleared, it's going to explore the phase one implementation again, so it's going to look at all the same stuff that we just cleared out of the context.

So that's what's annoying about clearing the context, right? Because we then have to spend 30 seconds just catching up with what the phase one implementation actually was.

Now by the time we're actually going to implement, nice, we're only at 15.5% context, well in the smart zone:

![Claude Code context showing 15.5% usage during implementation](https://res.cloudinary.com/total-typescript/image/upload/v1773322432/ai-hero-images/mrw2g6gytfilqxnwf0ko.png)

So I think we've got the picture now as to what it does when it's implementing, so I'll join you once it's finished implementing.

## Completing Phase 2

Okay, we have now finished phase two. That's pretty cool.

We've got a new analytics service, a dashboard component, a route and some tests. And as we can see on the analytics dashboard, we now have a chart here of sorts, and we have a per course breakdown at the bottom here.

![Analytics dashboard with revenue chart and per-course table](https://res.cloudinary.com/total-typescript/image/upload/v1773322436/ai-hero-images/rest7xbqatf0agiqwdx8.png)

Now, we do actually have a showstopper bug here, which is that there are no lines on the chart. You can hover over them by, you know, just doing this or whatever, but like, you can't actually see the data.

So I'm going to go back to Claude here, and I'm going to say, "you can't see any lines on the chart. Please add them," and I'm going to run this and I'm going to see what happens.

```
You can't see any lines on the chart. Please add them.
```

Now, I feel confident doing this within the same context window because we're only at like 30% here. We've got another 10% context window to play with:

![Showing 30% Context remaining](https://res.cloudinary.com/total-typescript/image/upload/v1773322438/ai-hero-images/oax7kuqto32h9qi1r6hx.png)

If I felt that we were straying into the dumb zone here I would clear the context and commit the code and then get it to create a new session based on just this bug probably. Or I might batch a bunch of bug fixes together so that it does them all together.

Okay, it's proposed a fix, and if we go and take a look at it, we can see that it's actually managed to find a really good fix. So if we look at 30 days, potentially, yes, we've got a nice little thing here. That's cool.

![Analytics chart now displaying revenue data with visible lines](https://res.cloudinary.com/total-typescript/image/upload/v1773322439/ai-hero-images/qityeauafjqpkk2dlxsd.png)

Now at this point I do have a lot of budget left, so I've still got, you know, I would say 10, 20% of context left. I could do some more QA on this commit before I commit it. Or I could just keep ploughing on with phase three and QA it all at the end.

So I'm going to commit this, and then I'm going to clear, and I'm going to complete phase three.

So I'm going to clear the context because that commit worked fine. And now I'll go upwards and I will go and do phase three instead.

And again I will see you when this has completed phasing.

## Completing Phase 3

Okay, all done. Here's a summary of what was implemented for phase three - admin access and empty states:

![](https://res.cloudinary.com/total-typescript/image/upload/v1773322440/ai-hero-images/lvmphlvft3pavge10ito.png)

We now have an admin route that enforces `userrole.admin`, validates the `instructorId`, okay. We've got a completed analytics service.

Time to get QA-ing, I think.

So I've gone to the application and the dev UI. I've logged in as Alex Rivera, who is the admin. I've gone to the manage users page here and I can see that there's a view analytics button next to the instructors:

![Admin manage users page with View Analytics button next to instructors](https://res.cloudinary.com/total-typescript/image/upload/v1773322441/ai-hero-images/ptmtdbpedpo1v7wbvc5p.png)

If we look at Marcus Johnson here, I can view his analytics too, but if I change to, why don't we change to James Park here, then it says that only admins can access this page.

![Admin analytics page showing 401 error for non-admin user](https://res.cloudinary.com/total-typescript/image/upload/v1773322442/ai-hero-images/mgbkqkrnyjasxxtkweiz.png)

I'm not really in love with this. I suppose this should probably be a 404 rather than a 401. In other words, we want to say this page doesn't exist instead of this page does exist and your attempt to hack in is not working.

But either way, that's something that can go on a backlog later.

But I am happy enough with this to call it done, I think.

## What We've Learned

And what you probably notice here is how hands-off the implementation stage actually is. There are certainly moments when we need to jump in and add our inputs and add our taste. But for the most part, because we've written such a clear destination, and we've specified the journey - the agent is basically just able to get on with it and it understands where it's going to go.

Now this approach scales to really, really big builds. All we need is a bit of a longer, more in-depth PRD and more time spent thinking about the journey there.

But once those two documents are in place and we've taken the time to think up a really good plan that involves tracer bullets and early feedback, then we can really start cooking.

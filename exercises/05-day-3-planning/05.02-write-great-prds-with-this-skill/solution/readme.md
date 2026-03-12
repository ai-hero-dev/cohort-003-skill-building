# Write Great PRDs With This Skill

## Understanding the Goal

Let me start by dictating what I actually want out of this PRD.

I want an instructor analytics dashboard primarily focused on revenue. I'd like to hammer out with you exactly what that entails and what that looks like.

Key constraints:

- Should obviously only be accessible to instructors
- Although admins should be able to see it too
- Instructors can only view analytics on their own courses
- Instructors should have a single analytics dashboard which displays the information for all of their courses

## Starting the Exploration

And predictably it's kicked off with an explore task here. I'm just going to let it complete so it can fill its context with everything in the repo that it needs.

```
● Explore(Explore codebase for PRD) Sonnet 4.6
  ⎿  Done (28 tool uses · 78.0k tokens · 1m 38s)
```

It's finished exploring. Now we begin the questioning.

## The Question and Answer Process

The first question is: what are the key revenue metrics you want displayed on the dashboard?

The LLM gives me options like total lifetime revenue, revenue per course, revenue over time, average order value, PPP discount impact, team versus individual purchase breakdown, and geographic breakdown by country.

I think I'm going to go with option two here: revenue totals plus time.

The next question is about time filters on the granularity of the revenue over time. Fixed periods like last 7 days, last 30 days, last 12 months look good to me.

**Should the dashboard include written enrollment metrics alongside revenue?** I think probably revenue plus enrollments plus ratings because we want to see student satisfaction data. That's really important.

Even in that first round of questions, I can feel the thing coming into life more. It really is crazy how beneficial these conversations are, just rubber ducking with a smart agent. And one that knows your codebase too. Very cool.

## Deciding on Layout

For the dashboard layout, the LLM asks: how should the per course data be presented?

I was imagining when I designed this a summary cards plus table. So you would have some summary cards at the very top and then a detailed table about all of the breakdowns. I think that makes most sense so I'm going to pick it.

For revenue over time, we probably do need a line chart, so we'll probably pull in a charting library.

For ratings, I think average plus count only makes sense.

## Building on Decisions

More questions come in.

For fixed time periods, I think seven days, 30 days, 12 months. This is for filtering the revenue trend line.

**Is an important one.** For the admin view should admin see a platform-wide analytics dashboard of all instructors or should they just be able to access any individual instructor's dashboard?

If we did a platform-wide analytics dashboard, that would be a massive increase in scope. Now we probably could do that as part of this PRD but it wasn't quite what I was envisaging.

I want the admins really to be able to view the instructor's dashboard just so they can see any issues with it, and so that they can act as the instructor just for debugging purposes. So I think for now, let's just save to view any instructor's view.

**Should the summary cards at the top of the dashboard also respect the selected time period or should they always show the all time totals?**

I use Stripe quite a lot and I have a feeling that Stripe respects the time filter. So I'm going to go with what Stripe does in this case.

Again, these are not easy decisions. The LLM asking us right now really is grilling us here.

## Wrestling With UI Decisions

Some of these questions, especially the UI ones, are really hard to answer, actually. And this is something that comes out during this planning stage, it's not necessarily simple to answer these in text.

What I would really like is a prototype to walk through here that would be the highest fidelity way to do it. So really you're having to use the power of your imagination to do this.

I'm going to go for the top one, which is just three cards at the top:

- Total revenue
- Total enrollments
- Average rating

Which column should appear in the per course table below the summary cards? I'm going to go detailed just to really max out that area.

And then how should admins access an instructor's analytics? They need a way to navigate to any instructor's dashboard. I think a link from the admin users page makes most sense there.

## The Implementation Questions

A few final questions on the chart details and some edge cases.

You know how this is like a brutal grilling, it's giving us here. It's so unbelievably useful because all of this conversation is going to end up inside the PRD.

For the line chart, x-axis granularity, last seven days should show daily points. What about the other periods? Let's auto scale it, so 12 months does monthly. All time is monthly. 30 days is daily. That makes sense.

The per course table should also be filtered by the selected period. I think this is a really good implementation question.

**Should the time period filter be stored in the URL as a search param or as client-side state?**

URL params mean the page is linkable, bookmarkable, which I love. So definitely in a URL search param.

If an instructor has no courses or no purchases yet, I think an empty state message makes sense here. Again, the empty state of this dashboard is not something I even considered going in. So having a question about it is really useful.

Just a couple more details to lock down.

When an admin clicks View Analytics for an instructor on admin users, what should the URL look like? That's a great point. I guess this doesn't really matter. I'll just put it in like this one I think.

The line chart should show revenue only. Should the per course table be sortable by clicking column headers? I think you probably do need it to be sortable.

Notice all of these questions and we're only at 15.6% context here. You know, this is not a context-heavy operation, really.

## Writing the PRD

Okay, I had to skip forward in time a little bit, but it's now ready to write the local file. So I'm just going to accept this edit and let's go and review the thing that we've just created.

```
● Write(prd/instructor-analytics-dashboard.md)
  ⎿  Wrote 116 lines to prd/instructor-analytics-dashboard.md
```

Now here's a little secret for you: I very rarely actually go and review the PRDs. What I do is I trust that the conversation that I've had with the LLM. I kind of get the sense that we share the same design idea, that we share a concept for what we're creating.

And so really all I'm doing when I review this, if I just give it a cursory glance, is just checking that that understanding is correct. I haven't really found a situation yet where it isn't correct. So all I'm doing here is double-checking the LLM's ability to summarize a conversation, which I know it can do really well.

But for the sake of this and for the sake of understanding what this PRD format does and how we might improve it, let's actually go and do this now.

## Reviewing the PRD

The problem statement is really good:

> There's no way for an instructor to see total revenue, revenue trends over time, or per course breakdowns. This makes it impossible for instructors to make informed decisions about pricing, marketing and course development.

The problem statement gives an overall why, which is really important for the implementation. When an agent has kind of like decisions to make while it's implementing, it can go back to the problem statement and understand why this feature even exists.

Then we have a dedicated analytics dashboard for instructors that provides a revenue focused overview. I think we kind of understand the solution here, and this is a nice summary of it.

And then this is the real juice: we have a numbered list of many, many user stories in this PRD.

## Understanding User Stories

Writing user stories is something you may have done as a professional developer. AI is really, really good at it.

You can think of these kind of like as acceptance criteria for what the final thing should look like. This is where we describe in detail what our destination is. But there are many, many different ways to frame this and phrase this.

For instance, the Gherkin language under the Cucumber project does this quite well. This is an actual coding language for specifying how these features should be put together. And since AI knows this quite well, you could use Gherkin here to specify exactly how these should work.

We also number these user stories so that we can later reference those numbers in the plan as a shorthand, which I find works really, really well.

For instance, number two is: **I want to see my total enrollment count across all courses for a selected time period so that I can gauge student interest.**

So for each story, we capture:

- The role (who's doing it)
- What they want to do
- Why they want to do it

Again, tying it back to the why, which is very important. Understanding why each decision is there, understanding why that decision was made is really important for anything implementing this. Because again, if it has any questions while it's implementing, it can go back to the why and hopefully use that to reason a bit better.

## The Implementation Plan

If we fold up the user stories, we can see then we have a list of implementation decisions.

First of all, a list of modules:

- A new analytics service
- A couple of new routes for the instructor analytics
- A shared analytics dashboard component

You note here that it's not providing implementation suggestions here. It's just kind of saying these are the high level modules that we're going to create.

Then we've got a list of technical decisions down below.

| Decision               | Details                                                                                      |
| ---------------------- | -------------------------------------------------------------------------------------------- |
| Table sorting          | Client side                                                                                  |
| Per course table       | Respects the time filter                                                                     |
| Time chart granularity | Daily data points for 30 days and seven days, monthly data points for 12 months and all time |

## Schema and Testing

Then below that, we have some schema changes, some kind of testing decisions as well, which I really like.

We're specifically saying what to test inside here. We've got some prior art. Then we've got some out of scope stuff.

And this is actually really detailed. This is basically the negative space of all of the positive decisions we had, where we said okay, we do this and not this.

For example:

- PPP discount impact analysis
- Team versus individual purchase breakdown
- All of this stuff is actually ideas that you could take further and have their own PRD created later

## Final Notes

And finally, I just like having this further notes section at the bottom here. So this is just for any kind of stuff that doesn't fit into the top sections.

And so there we go. We have successfully described the destination for where we want to go with this analytics dashboard.

And hopefully, if you walk through a similar process to me, then you should end up with a similarly detailed document. You might have slightly different emphases in your document. The sections might be a slightly different lengths. But it will probably follow a template like this.

And like me, you are probably now itching to see this come to life and actually build something from it.

So nice work. I will see you in the next one.

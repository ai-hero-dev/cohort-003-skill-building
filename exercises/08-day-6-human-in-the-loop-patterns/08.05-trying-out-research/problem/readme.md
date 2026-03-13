# Trying Out Research

## Introduction

Now that you understand what research is, it's time to actually do it. You're going to build a live presence indicator for lessons - those little icons showing who else is taking the course right now.

There are many ways to solve this problem. You could use simple polling, WebSockets, or an external service. Each approach has different tradeoffs, and you need to know when someone joins or leaves so you can update the UI.

Instead of guessing which approach is best, you're going to use Claude Code to research the options together, ask good questions about the constraints, validate assumptions against real-world data, and then document your findings.

## Steps To Complete

### Set Up Your Research Prompt

- [ ] Open Claude Code in your project

Ask Claude to help you research several different approaches to creating a live presence indicator. In your prompt, be specific about what you need.

```
I want to research several different approaches to create a live presence indicator.

This live presence indicator is going to show up for students who are intrigued and want to know who else is looking at the lesson at the same time.

I want you to iterate with me towards a solid approach and ask me some good questions about where we should go. Then I want you to look on the web to back things up and kind of validate our assumptions.

At the end, I want you to create a research document inside the plans directory. This document should be focused on the implementation and how we intend to use it.
```

### Work With Claude Code As A Research Partner

- [ ] Let Claude ask you clarifying questions about your constraints

Think about questions like: How many concurrent users do you expect? How real-time does the indicator need to be? Do you care about seeing when someone quits the lesson immediately, or is a slight delay acceptable? What's your backend infrastructure like?

- [ ] Discuss the tradeoffs between different approaches

As Claude presents options, push back on the assumptions. Ask why one approach might be better than another. Write down anything you notice.

- [ ] Research at least 3-4 different approaches together

Polling, WebSockets, Server-Sent Events, and external services like Pusher are all worth exploring. Claude should look these up on the web and validate whether they're actually viable.

### Review and Iterate

- [ ] Read through Claude's research findings carefully

Does the analysis make sense given what you know about your project? Are there any assumptions that don't match your actual constraints?

- [ ] Ask follow-up questions if needed

Push Claude to explain why it recommends a particular approach. Make it justify its decision based on your specific requirements.

### Create the Research Document

- [ ] Have Claude create a markdown research document in your plans directory

This document should include:

- The different approaches evaluated
- The pros and cons of each approach
- Your chosen approach and why you selected it
- Implementation notes for how you'll actually use it

- [ ] Review the markdown document

Make sure it accurately reflects your decision-making process and is detailed enough that you could hand it to another engineer to implement from.

- [ ] Ask Claude to commit the research document to git

Tell Claude to stage and commit the research document. You can ask it to do this in your same conversation.

```
Can you commit this research document? Use a clear commit message like "docs: research on live presence indicator approaches"
```

### Test Your Process

- [ ] Reflect on how the research process went

Did asking Claude good questions help you arrive at a better decision? What would you do differently next time?

- [ ] (Optional) Share your findings in the Discord

If you want feedback on your approach or hit any interesting insights, the community would love to hear about it.
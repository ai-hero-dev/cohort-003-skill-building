# Managing Your Claude Code Session

You're about to start using Claude Code for the first time. Before diving into advanced workflows, you need to know the basics: how to send prompts, monitor what's happening in your session, and control execution.

This lesson is pure mechanics. You'll learn *where* the buttons are and *what they do*, not *when* to push them or *why* you might need them. That strategy comes later.

By the end, you'll be comfortable opening Claude Code, sending it a question, checking what's happening under the hood, interrupting if needed, and clearing your session when you want a fresh start.

## Steps To Complete

### Send Your First Prompt

- [ ] Open Claude Code and make sure you can see the input area where you type prompts

- [ ] Type the prompt: `Which package manager am I using?`

This is a real question about your actual project, so Claude Code can look at your repository and give you an answer.

- [ ] Submit your prompt and wait for Claude to respond

You should see Claude analyzing your project files and telling you which package manager it found.


### Check Your Session Usage

- [ ] Run the `/usage` command

Type `/usage` into Claude Code and submit it just like you would a regular prompt.

- [ ] Observe what information `/usage` shows you

You'll see data about how much of your Claude account quota you've consumed. This is useful for monitoring, though you don't need to act on it right now. Just know it's there.


### Check Your Session Context

- [ ] Run the `/context` command

Type `/context` and submit it.

- [ ] Look at what information it displays

You'll see details about what Claude currently "remembers" from this session. All the prompts you've sent and responses it's given you will be shown. This is the memory of your current conversation.


### Interrupt a Long Task

- [ ] Send a time-consuming prompt like: `Analyze the structure of this codebase in detail`

Claude will start working and generating a lengthy response.

- [ ] While Claude is still working, interrupt the execution

Look for the interrupt button or use the keyboard shortcut to stop Claude mid-response. Check the Claude Code interface for where this control is located.

- [ ] Confirm that Claude stops generating

You should see the response cut off and the execution halted.


### Clear and Verify the Reset

- [ ] Run the `/clear` command to wipe your session memory

Type `/clear` and submit it.

- [ ] Run `/context` again to see that your session memory has been reset

Compare what you see now to what `/context` showed you earlier. Your session history should be empty or cleared.

- [ ] Notice the difference between before and after

This makes the "clear" action concrete instead of abstract. You can see the reset actually happened.


### Send a Final Prompt

- [ ] Type a new prompt, like: `Say hello`

This confirms your session is still working normally after clearing.

- [ ] Submit it and see the response

You've now completed the full cycle: send, monitor, interrupt, clear, and resume. You're ready to move forward with Claude Code.
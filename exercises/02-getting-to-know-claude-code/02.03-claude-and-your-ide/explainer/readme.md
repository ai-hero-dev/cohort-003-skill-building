# Claude And Your IDE

When you're working with Claude Code, you'll want it to integrate smoothly with your development environment. The IDE integration isn't just a nice-to-have - it shapes how you interact with Claude's output, especially when it comes to managing code changes.

The most useful part comes from how Claude Code handles diffs. Instead of showing changes in a hard-to-read terminal format, your IDE displays them in a rich, interactive way. You can scroll through files, review changes line-by-line, and even make tweaks before accepting them.

## Steps To Complete

### Set Up Your IDE Integration

- [ ] Run the `/ide` command in Claude Code

This command shows your IDE connection status and guides you through installation if needed.

```
/ide
```

The output tells you which IDE you're connected to and provides installation instructions for other supported IDEs like Cursor, Windsurf, or others.

- [ ] Install the Claude Code extension for your IDE

Claude Code communicates with your IDE through an extension. If you're using VS Code, the extension is called "Claude for VS Code". Follow the installation link from the `/ide` command output.

- [ ] Press enter to confirm and close the IDE status check

Once installed and connected, your IDE is ready to handle diffs from Claude Code.


### Experience Diff Management In Your IDE

- [ ] Ask Claude Code to make a file change

For example, try this prompt:

```
Remove the test watch command from package.json
```

- [ ] Watch Claude Code read and modify your file

Claude will read the relevant file (in this case, `package.json`) and propose changes.

- [ ] Close the terminal diff view and observe the change in your IDE

Instead of seeing a confusing diff in the terminal, you'll see the proposed change appear directly in your IDE's editor. This gives you a much richer experience.

- [ ] Review the change in context

The IDE view lets you scroll through the file, see surrounding code, and understand exactly what Claude is changing.

- [ ] Accept or modify the change

You can either:
- Click the "Accept Proposed Changes" button in your IDE
- Manually edit the file and save it to accept the changes
- Reject the changes entirely and ask Claude to try again

### Understand When To Use IDE Integration

- [ ] Recognize that IDE integration primarily powers diff management

This is the feature that shows up most often and delivers the most value.

- [ ] Notice that you can tweak Claude's output before accepting it

Sometimes Claude's suggestions are close but not quite right. Having the full IDE context lets you make quick adjustments without re-running the prompt.

- [ ] Understand that your IDE provides better visibility than the terminal

A proper code editor with syntax highlighting, line numbers, and file context is vastly superior to reading diffs in a terminal.
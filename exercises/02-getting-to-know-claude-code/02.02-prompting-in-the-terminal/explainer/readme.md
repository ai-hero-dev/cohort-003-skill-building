# Prompting In The Terminal

When you're working with Claude Code, you'll want to give Claude exactly the right context to succeed. The better you can reference files, manage your prompts, and provide visual context, the better results you'll get.

This lesson covers several practical techniques to improve how you communicate with Claude in the terminal.

## Steps To Complete

### Referencing Files With The @ Symbol

- [ ] Open Claude Code and start typing a new prompt

When you want Claude to focus on specific files, use the `@` symbol to reference them directly.

- [ ] Type `@` and start typing a filename

You'll see autocomplete suggestions appear. For example, typing `@routes` might show you `routes.ts`.

- [ ] Navigate through the suggestions using the arrow keys

Use the up and down arrow keys to browse available files.

- [ ] Press `Tab` to select a file

Once you've found the file you want, press `Tab` to add it to your prompt.

- [ ] Add multiple files by repeating the process

You can reference as many files as you need in a single prompt. Type `@` again and repeat the steps above for each additional file.

```
Tell me about @routes.ts and @schema.ts
```

When you run this prompt by pressing `Return`, Claude automatically reads both files into the context window. This saves Claude from having to find them manually, and gives it exactly what it needs to help you.

### Stashing Commands With Control+S

Sometimes you're working on a complex prompt, but you realize you need to ask Claude something else first. Instead of losing your work, you can stash it.

- [ ] Write a detailed prompt in Claude Code

- [ ] Press `Ctrl+S` to stash the prompt

Your prompt is now saved in Claude's memory and won't be submitted.

- [ ] Type a new prompt and press `Return` to submit it

```
@myfile.ts - why is this broken?
```

- [ ] After Claude responds, your stashed prompt automatically reappears

You can now continue where you left off.

- [ ] Press `Return` to submit your stashed prompt

This is especially useful when you need to give Claude feedback on something, realize you need to provide more context first, and don't want to lose your original detailed instructions.

### Clearing Stashed Commands

If you stash a prompt and then decide you don't need it anymore, you can delete it.

- [ ] Press `Ctrl+C` to clear the stashed command

The prompt is removed and you're back to a blank input field.

### Adding Images To Your Prompts

Claude can analyze images, which is useful when you need to discuss visual designs, screenshots, or other image-based content.

- [ ] Copy an image from your computer or the web

Right-click on the image and select "Copy image" from the context menu.

- [ ] Click in the Claude Code input field and paste the image

Press `Ctrl+V` (on Mac as well) to paste.

- [ ] Type your prompt below or above the image

```
What location is this? Tell me about it.
```

- [ ] Press `Return` to submit

Claude will analyze the image and respond to your question about it.

**Note:** Image pasting works on most systems, but may not work on Windows Subsystem for Linux (WSL).

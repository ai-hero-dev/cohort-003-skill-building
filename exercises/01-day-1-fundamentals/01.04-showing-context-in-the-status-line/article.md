# Creating The Perfect Claude Code Status Line

I think I've created the perfect Claude code status line:

```
matt/course-video-manager | main | S: 0 | U: 1 | A: 0 | 17.3%
```

First, it has the repo that I'm working on relative to my repository's directory (`matt/course-video-manager`). If you're like me, you probably have a single directory that has all of your repositories on.

So I have it set up in my status line just to show the relative path based on my `~repos/` directory.

Then I have some Git information:

```
main | S: 0 | U: 1 | A: 0
```

I have the branch that I'm on and I have the staged, unstaged, and added changes. This is kind of optional, but I do like it just to be able to, when I'm only working in the terminal and you're not using an IDE, see what's happening in Git at all times.

And then finally, and this is the most important one, is the percentage of context window that I've used up in this session:

```
17.3%
```

This is a constant source of paranoia for me. I always want to be using the minimum amount of context I can, because the more you put in the context window, the worse the AI is going to be.

Having this constantly at my fingertips and monitoring it going, "Ooh, I think about 60 is probably where I want to stop" is just amazing.

## How It's Set Up

The way this is set up is by using this `settings.json` file inside `.claude` directory:

```json
{
  "hooks": {}
```

You can see it runs `bash ~/.claude/statusline-wrapper.sh`. This status line wrapper basically takes one status line command script.

Then we also take the output from a CLI called `ccStatusLine`. This basically lets me get the context percentage from it:

```json
{
  "version": 3,
  "lines": [
    [
      {
        "id": "1",
        "type": "context-percentage",
        "color": "yellow",
        "bold": true,
        "rawValue": true
      }
```

Then we combine the outputs of these files.

## Try It Yourself

If you want to configure this yourself, here's how to set it up.

### Step 1: Install ccstatusline

First, install the ccstatusline package globally:

```bash
npm install -g ccstatusline
```

### Step 2: Configure ccstatusline

Create the config file at `~/.config/ccstatusline/settings.json`:

```json
{
  "version": 3,
  "lines": [
    [
      {
        "id": "1",
        "type": "context-percentage",
        "color": "yellow",
        "bold": true,
        "rawValue": true
      }
    ],
    [],
    []
  ],
  "flexMode": "full-minus-40",
  "compactThreshold": 60,
  "colorLevel": 2,
  "inheritSeparatorColors": false,
  "globalBold": false,
  "powerline": {
    "enabled": false,
    "separators": [""],
    "separatorInvertBackground": [
      false
    ],
    "startCaps": [],
    "endCaps": [],
    "autoAlign": false
  }
}
```

The key part here is `"rawValue": true` which shows just the percentage without the "Ctx:" label, and `"bold": true` to match the color of the git numbers.

### Step 3: Create the Git Status Script

Create `~/.claude/statusline-command.sh`:

```bash
#!/bin/bash

# Read JSON input
input=$(cat)

# Extract values from JSON (without jq)
cwd=$(echo "$input" | sed -n 's/.*"current_dir":"\([^"]*\)".*/\1/p')

# Git information (skip optional locks for performance)
if git -C "$cwd" rev-parse --git-dir > /dev/null 2>&1; then
  # Get repo name relative to ~/repos/
  repo_name=$(echo "$cwd" | sed "s|^$HOME/repos/||")

  # Get branch
  branch=$(git -C "$cwd" --no-optional-locks rev-parse --abbrev-ref HEAD 2>/dev/null)

  # Count staged files
  staged=$(git -C "$cwd" --no-optional-locks diff --cached --name-only 2>/dev/null | wc -l)

  # Count unstaged files (modified + deleted, not untracked)
  unstaged=$(git -C "$cwd" --no-optional-locks diff --name-only 2>/dev/null | wc -l)

  # Count untracked files
  untracked=$(git -C "$cwd" --no-optional-locks ls-files --others --exclude-standard 2>/dev/null | wc -l)

  printf '\033[01;36m%s\033[00m | \033[01;32m%s\033[00m | S: \033[01;33m%s\033[00m | U: \033[01;33m%s\033[00m | A: \033[01;33m%s\033[00m' \
    "$repo_name" "$branch" "$staged" "$unstaged" "$untracked"
else
  # Not a git repo
  printf '\033[01;36m%s\033[00m' "$cwd"
fi
```

**Note:** Change `~/repos/` on line 12 if your repositories live in a different directory.

### Step 4: Create the Wrapper Script

Create `~/.claude/statusline-wrapper.sh`:

```bash
#!/bin/bash

# Read JSON input once
input=$(cat)

# Get git info from existing script
git_info=$(echo "$input" | bash ~/.claude/statusline-command.sh)

# Get context percentage from ccstatusline
context_pct=$(echo "$input" | npx ccstatusline)

# Combine outputs
printf '%s | %s' "$git_info" "$context_pct"
```

### Step 5: Make Scripts Executable

```bash
chmod +x ~/.claude/statusline-command.sh
chmod +x ~/.claude/statusline-wrapper.sh
```

### Step 6: Update Claude Settings

Add this to your `~/.claude/settings.json`:

```json
{
  "statusLine": {
    "type": "command",
    "command": "bash ~/.claude/statusline-wrapper.sh"
  }
}
```

### Step 7: Restart Claude Code

Restart Claude Code to see your new status line in action!

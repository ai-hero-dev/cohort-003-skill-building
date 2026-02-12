# Showing Context In The Status Line

Claude Code doesn't show your context window usage by default. You need to set this up yourself if you want to monitor it constantly while you're coding.

Having that number right in your status line, visible at a glance, gives you the feedback you need to make good decisions about your session.

## Steps To Complete

### Configure ccstatusline

- [ ] Create the config directory and file

```bash
mkdir -p ~/.config/ccstatusline
```

Then create `~/.config/ccstatusline/settings.json` with this content:

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
    "separatorInvertBackground": [false],
    "startCaps": [],
    "endCaps": [],
    "autoAlign": false
  }
}
```

The key settings here are `"rawValue": true` (shows just the percentage number) and `"bold": true` (makes it stand out).


### Create the Wrapper Script

- [ ] Create the Claude scripts directory

```bash
mkdir -p ~/.claude
```


- [ ] Create `~/.claude/statusline-wrapper.sh`

```bash
#!/bin/bash

# Read JSON input
input=$(cat)

# Get context percentage from ccstatusline
context_pct=$(echo "$input" | npx ccstatusline)

# Output just the percentage
printf '%s' "$context_pct"
```


- [ ] Make the script executable

```bash
chmod +x ~/.claude/statusline-wrapper.sh
```

This script reads your Claude Code session data and pipes it to `ccstatusline` to extract the percentage.


### Update Claude Code Settings

- [ ] Open `~/.claude/settings.json`

If this file doesn't exist yet, create it.


- [ ] Add the status line configuration

```json
{
  "statusLine": {
    "type": "command",
    "command": "bash ~/.claude/statusline-wrapper.sh"
  }
}
```

Preserve any other settings that might already exist in this file.


### Test Your Setup

- [ ] Restart Claude Code completely

Close the application fully and reopen it.


- [ ] Check your status line

You should now see a yellow, bold percentage (like `17.3%`) displayed in your Claude Code status line. This number updates as your context window fills during your session.
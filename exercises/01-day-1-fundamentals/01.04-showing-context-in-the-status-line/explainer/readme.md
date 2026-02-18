# Showing Context In The Status Line

Claude Code doesn't show your context window usage by default. You need to set this up yourself if you want to monitor it constantly while you're coding.

Having that number right in your status line, visible at a glance, gives you the feedback you need to make good decisions about your session. We'll use [`ccstatusline`](https://www.npmjs.com/package/ccstatusline), a community tool that formats Claude Code's session data into a clean status line.

## Steps To Complete

### Configure ccstatusline

- [ ] Create the config directory

```bash
mkdir -p ~/.config/ccstatusline
```

- [ ] Create `~/.config/ccstatusline/settings.json` with this content:

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

### Update Claude Code Settings

- [ ] Open `~/.claude/settings.json`

If this file doesn't exist yet, create it.

- [ ] Add the status line configuration

```json
{
  "statusLine": {
    "type": "command",
    "command": "npx ccstatusline@latest"
  }
}
```

Preserve any other settings that might already exist in this file. Claude Code pipes session data to this command automatically — `ccstatusline` reads it and outputs the formatted status line.

### Test Your Setup

- [ ] Restart Claude Code completely

Close the application fully and reopen it.

- [ ] Check your status line

You should now see a yellow, bold percentage (like `17.3%`) displayed in your Claude Code status line. This number updates as your context window fills during your session.

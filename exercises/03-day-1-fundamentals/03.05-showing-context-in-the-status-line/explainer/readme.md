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
        "type": "context-length",
        "color": "yellow",
        "bold": true,
        "rawValue": true
      },
      {
        "id": "2",
        "type": "custom-text",
        "customText": "(",
        "color": "brightBlack",
        "merge": "no-padding"
      },
      {
        "id": "3",
        "type": "context-percentage",
        "color": "brightBlack",
        "rawValue": true,
        "merge": "no-padding"
      },
      {
        "id": "4",
        "type": "custom-text",
        "customText": ")",
        "color": "brightBlack",
        "merge": "no-padding"
      }
    ],
    [],
    []
  ],
  "flexMode": "full-minus-40",
  "compactThreshold": 60,
  "colorLevel": 2,
  "defaultSeparator": " ",
  "inheritSeparatorColors": false,
  "globalBold": false,
  "powerline": {
    "enabled": false,
    "separators": [" "],
    "separatorInvertBackground": [false],
    "startCaps": [],
    "endCaps": [],
    "autoAlign": false
  }
}
```

This configures four widgets on one line: a bold yellow token count (`context-length`), followed by a dimmed percentage in parentheses. The `"merge": "no-padding"` on the parentheses and percentage widgets glues them together without extra spacing, while `"defaultSeparator": " "` adds a space between the token count and the opening parenthesis. `"rawValue": true` strips the labels so you get clean numbers.

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

You should now see a bold yellow token count followed by a dimmed percentage (like `186.2k (17.3%)`) displayed in your Claude Code status line. These numbers update as your context window fills during your session.

---
name: browser
description: When testing or verifying web UI use this skill to start the browser server, take screenshots to observe state, interact with elements, and verify visually.
---

## Useful skills

1. scientific-method (for more thorough investigation/debugging)

## Setup

If not running already:

```bash
# Start dev server
npm run dev # or your project's dev command

# Start browser server
python .opencode/skill/browser/screenshot.py start &

# Check status
python .opencode/skill/browser/screenshot.py status
```

## Teardown

Stop any processes you started:

```bash
python .opencode/skill/browser/screenshot.py stop
# Kill any dev servers you started
```

## Commands

```bash
python .opencode/skill/browser/screenshot.py <command> [args]
```

| Command | Description |
|---------|-------------|
| `start` | Start browser server |
| `stop` | Stop browser server |
| `status` | Check if running |
| `screenshot` | Take screenshot |
| `click <selector>` | Click element |
| `type <selector> <text>` | Type into input |
| `press <key>` | Press key (Enter, ArrowDown, etc.) |
| `list <selector>` | List matching elements |
| `text <selector>` | Get element text |

## Workflow

1. Screenshot to see current state
2. List elements to discover selectors
3. Interact with elements
4. Screenshot to verify result
5. Run teardown before ending session

## Screenshots

Saved to `.screenshots/screenshot.png` in the current working directory. Read this file to see the visual state.

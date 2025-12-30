# dotopencode

Shared [OpenCode](https://opencode.ai) configuration with custom agents, commands, and skills.

## What's Included

### Agents

| Agent | Description |
|-------|-------------|
| `architect` | Plans architecture and major changes |
| `critic` | Adversarial critic for generating insights through disagreement |
| `delegate` | Orchestrates long-horizon projects via work packages and subagents |
| `document` | Technical writer for documentation |
| `ux` | Tests web interfaces and researches UX solutions |

### Commands

| Command | Description |
|---------|-------------|
| `/browser-test` | Test web UI in browser with screenshots |
| `/commit` | Create a git commit with AI-generated message |
| `/review-docs` | Check documentation accuracy against code |
| `/test-and-fix` | Run tests and fix any failures |

### Skills

| Skill | Description |
|-------|-------------|
| `browser` | Take screenshots and interact with web UIs via Playwright |
| `read-learnings` | Review previously recorded project learnings |
| `record-learnings` | Record notable discoveries for future reference |
| `scientific-method` | Hypothesis-driven iteration for debugging and verification |
| `work-packages` | Structured approach for multi-agent task handoff |
| `write-tests` | Guidelines for writing tests |

## Setup

### Option 1: Symlink (Full Replacement)

Replace your global OpenCode config with this repo:

```bash
# Clone the repo
git clone https://github.com/djgrant/dotopencode.git ~/repos/dotopencode

# Back up existing config (if any)
mv ~/.config/opencode ~/.config/opencode.bak

# Symlink
ln -s ~/repos/dotopencode ~/.config/opencode
```

### Option 2: OPENCODE_CONFIG_DIR (Merge with Personal Config)

Keep your personal config at `~/.config/opencode` and load this repo as an overlay:

```bash
# Clone the repo
git clone https://github.com/djgrant/dotopencode.git ~/repos/dotopencode

# Add to your shell profile (.zshrc, .bashrc, etc.)
export OPENCODE_CONFIG_DIR=~/repos/dotopencode
```

The overlay config is loaded **after** your personal config, so it can override settings while preserving your personal preferences.

## Browser Skill Setup

The browser skill requires Playwright:

```bash
pip install playwright
playwright install chromium
```

Then start the browser server before using browser commands:

```bash
python ~/.config/opencode/skill/browser/screenshot.py start
```

## Customization

### Per-Project Overrides

You can override any of these settings in a project's `.opencode/` directory. OpenCode merges configs in this order:

1. Global config (`~/.config/opencode/`)
2. `OPENCODE_CONFIG_DIR` (if set)
3. Project config (`.opencode/`)

### Adding Your Own

- **Agents**: Add `.md` files to `agent/`
- **Commands**: Add `.md` files to `command/`
- **Skills**: Add directories with `SKILL.md` to `skill/`

## Work Packages

This config includes a work package system for structured multi-agent collaboration:

```
work/
  todo/        # Pending work packages
  in-progress/ # Currently being worked on
  completed/   # Finished work packages
```

Work packages are markdown files that define a problem, scope, approach, and track results across multiple agent sessions.

## Learnings

Agents can record project-specific discoveries in `learnings/`:

```
learnings/
  2025-01-15-(package:api)-(auth flow)-(tags:security,oauth).md
```

These are loaded by the `read-learnings` skill to provide context to agents.

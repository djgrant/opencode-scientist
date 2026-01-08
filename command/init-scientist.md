# /init-scientist

Initialize project with the-scientist directory structure.

## Instructions

You are setting up a project to use the-scientist configuration. Follow these steps:

### 1. Check Current State

Check the following and note what exists vs what's missing:

- `.opencode/work/` directory structure (todo/, in-progress/, completed/)
- `.opencode/learnings/` directory
- `AGENTS.md` or `.opencode/agents.md` file

### 2. Propose a Plan

Present your findings to the user in a clear summary:

```
## Current State

Directories:
- .opencode/work/: [exists | missing]
- .opencode/learnings/: [exists | missing]

AGENTS.md: [exists at ./AGENTS.md | exists at .opencode/agents.md | missing]

## Proposed Actions

1. [List what will be created]
```

Then ask the user:
- "Would you like me to create an AGENTS.md file? (default location: ./AGENTS.md)"
- "Proceed with setup? (y/n)"

Wait for user confirmation before proceeding.

### 3. Execute the Plan

After user confirms:

**Create directory structure:**
```bash
mkdir -p .opencode/work/todo .opencode/work/in-progress .opencode/work/completed
mkdir -p .opencode/learnings
touch .opencode/work/todo/.gitkeep
touch .opencode/work/in-progress/.gitkeep
touch .opencode/work/completed/.gitkeep
touch .opencode/learnings/.gitkeep
```

**Create AGENTS.md (if requested):**

Create the file at the user's preferred location with this template:

```markdown
# Project Instructions

## Overview

[Brief description of the project]

## Architecture

[Key architectural decisions and patterns]

## Development Guidelines

[Coding standards, conventions, and practices]

## Important Files

[Key files and their purposes]
```

### 4. Report Results

Summarize what was done:

```
## Setup Complete

Created:
- .opencode/work/todo/
- .opencode/work/in-progress/
- .opencode/work/completed/
- .opencode/learnings/
- [AGENTS.md if created]

Skipped:
- [List anything that already existed]
```

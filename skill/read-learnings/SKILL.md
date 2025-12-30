---
name: read-learnings
description: When starting a task or needing context about past decisions, use this skill to review previously recorded learnings
---

# Reading Learnings

Review learnings recorded in `.opencode/learnings/` before starting work.

## When to Use

- At the start of a complex task
- When encountering an unfamiliar pattern
- Before making architectural decisions
- When debugging issues that may have been encountered before

## How to Read

### 1. List All Learnings

```bash
ls .opencode/learnings/
```

### 2. Read Relevant Files

Use the Read tool to view the full content of any learning file that looks relevant to your task.

## File Format

Learnings follow this naming convention:
```
{yyyy-mm-dd}-(package:{package})-({title})-(tags:{tags}).md
```

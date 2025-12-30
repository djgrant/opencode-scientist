---
name: record-learnings
description: When you learn something particularly notable, use this skill to record it
---

When you learn something notable (i.e. not general knowledge, normally something specific to the project), and deem that it could be useful to your future self, record the learning for posterity.

### Adding Learnings

Learning documents are store in ./.opencode/learnings.

Each document should be understood by its filename:

*Template*: `{yyyy-mm-dd}-(package:{package})-({title})-(tags:{tags}).md`
*Example*: `2025-12-25-(package:core)-(event ordering)-(tags:adapators,emit,sync).md`

The document should contain metadata and a very concise record of the learning:

```markdown
---
date: yyyy-mm-dd
package: core | create | etc.
tags:
 - tag 1
 - tag 2
---

# [title]

[One or two sentences. No more than needed.]
```

### Codebase Knowledge

For updating general information about the codebase, do not use the learning directory. Instead, update ./.opencode/agents.md directly.

When updating agents.md, ensure you follow these best practices:

- Make surgical edits, don't rewrite sections
- Preserve existing structure
- Reference specific code when possible
- Keep it very concise
- Do not modify vision without consulting the user

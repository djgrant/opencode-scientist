# MDZ Language Specification (Compact)

MDZ extends Markdown with a logic layer for LLM evaluation. It interleaves **Host Text** (raw Markdown) and **MDZ Blocks** (statements).

## Core Syntax
- **Case-Sensitive**: Keywords are `ALL CAPS`.
- **Indentation-Insensitive**: Layout is for presentation only.
- **List Markers**: Statements can optionally be prefixed with `- ` to preserve indentation in editors.
- **Host Text**: Anything not starting with a keyword is treated as raw text (prose).

## Variables & Types
- **Assignment**: `$var = value` or `$var: Type = value`
- **Push**: `$array << value`
- **Type Declaration**: `TYPE Name = "enum" | "val"` or `TYPE Name = (String, Number)`
- **Types**: `Number` (`1`, `1.5`), `String` (`"text"`, `"fmt #{var}"`), `Array<T>` (`["a", "b"]`), `Tuple<T...>` (`("a", 1)`), `Link` (`~/path`, `#anchor`), `Lambda` (`x => x`).
- **Semantic Expressions**: Unquoted text in value positions is inferred by context (e.g., `$summary = the main argument`).

## Control Flow
**FOR Loop**
```md
FOR $item IN $list DO
  ...
END
```
**WHILE Loop**
```md
WHILE $x > 0 DO
  ...
END
```
**IF Conditional**
```md
IF $x = 1 AND $y != 2 THEN
  ...
ELSE
  ...
END
```
**CASE Switch**
```md
CASE $status
WHEN "draft" THEN ...
WHEN "published" THEN ...
ELSE ...
END
```
**Block/Prose Wrapper**
```md
DO
  Raw prose here
END
```

## Composition
**SPAWN (Delegate)**
```md
SPAWN ~/agent/name TO instruction text
SPAWN ~/agent/name WITH #anchor
ASYNC SPAWN ...
```
**USE (Tool/Skill)**
```md
USE ~/skill/name TO instruction
USE ~/skill/name WITH
  param1: value
```

## Operators
- **Comparison**: `=`, `!=`
- **Logic**: `AND`, `OR`, `NOT`
- **Usage**: Only valid in conditions (`IF`, `WHILE`, `WHEN`). Elsewhere is text.

## Examples

### Complex Logic
```md
FOR $file IN $files
  - IF $file = "important.txt" THEN
      SPAWN ~/agent/analyzer WITH $file
  - ELSE
      $status = skip this file
  - END
END
```

### Semantic Assignment
```md
$summary = summarize the conversation
USE ~/skill/logger WITH
  message: $summary
```

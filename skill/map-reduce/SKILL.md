---
name: "map-reduce"
description: "When it would yield better results to explore mulitple approaches to a problem, load this skill to orchestrate multiple agents using a diverge and converge strategy."
---

## ::types::

TYPE Task = instructions for a sub-agent to execute
TYPE Strategy = "accumulate" | "independent"

### ::input::

$transform: Task
$validator: Task
$strategy: Strategy = "accumulate"
$maxIterations: Number = 5

## ::context::

$statusQuo: Link
$iteration: Number = 0

## ::workflow::

USE ~/skill/work-packages TO create master work package

DO
  Summarise status quo into $statusQuo
END

IF $strategy = "accumulate" THEN
  SPAWN ~/agent/general TO run accumulate prompt WITH #accumulate-prompt
ELSE
  SPAWN ~/agent/general TO run independent prompt WITH #independent-prompt
END

RETURN $statusQuo

## Accumulate Prompt

```mdz
WHILE $iteration < $maxIterations AND NOT diminishing returns DO
  AWAIT SPAWN ~/agent/general TO $transform WITH
    input: $statusQuo
    output: next candidate path
  AWAIT SPAWN ~/agent/general TO $validator WITH
    candidate: next candidate path
  IF validation passed THEN
    $statusQuo = next candidate path
  END
  $iteration = $iteration + 1
END

RETURN $statusQuo
```

## Independent Prompt

```mdz
WHILE $iteration < $maxIterations DO
  ASYNC SPAWN ~/agent/general TO $transform WITH
    iteration: $iteration
    output: candidate path
  $iteration = $iteration + 1
END

AWAIT SPAWN ~/agent/general TO $validator WITH
  candidates: candidate paths from async runs

RETURN winning candidate
```

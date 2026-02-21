---
name: work-packages
description: When creating or working on a work package (WP), load this skill to get templates and understand the WP lifecycle.
---

Work packages are a type of task that we use for tracking progress state between agent sessions. 

This skill defines what to put in the task, not how to create the task.

Work packages can either by for a complete feature (#master-work-package-template), or a scoped task (#scoped-work-package-template).

## Work Package Lifecycle

1. Create a work package using the available task management tools
2. Change state to in progress when starting
3. Record results
4. Iterate until 
5. Change state to completed when done

## Master Work Package Template

```md
# {Title}

## Goal
{What needs to be solved}

## Hypothesis
{Why you think this will work (or not work)}

## Validation
{How you will measure and test the results}

## Results
To be filled out upon completion. Can contain multiple iterations.

## Evaluation
What did your learn from the results? Was the hypothesis proved correct?
```

## Scoped Work Package Template

```md
# {Title}

## Goal
{What needs to be solved}

## Scope
{What is in or out of scope; what will be affected}

## Hypothesis
{Why you think this will work (or not work)}

## Approach
{How you intend to achieve the goal}

## Validation 
{How you will measure and test the results}

## Results
To be filled out upon completion. Can contain multiple iterations.

## Evaluation
What did your learn from the results? Was the hypothesis proved correct?
```

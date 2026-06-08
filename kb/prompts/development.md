---
id: "prm-002"
type: "prompt"
created: "2026-01-18"
updated: "2026-01-18"
status: "active"
tags:
  - "development"
  - "debugging"
---

# Prompts: Development

> Example file. Replace with your own.

## Reproduce-then-fix

**Use case:** fixing a bug without guessing.

```text
Before changing any code: write a failing test that reproduces {{bug}}. Show me
the test and the failure output. Only then propose the minimal fix, and confirm
the test passes after.
```

**Notes:** forces a verifiable goal before edits.

## Minimal-diff refactor

**Use case:** cleaning up code without scope creep.

```text
Refactor {{target}} for clarity only. Do not change behavior or public API. Keep
the diff minimal; every changed line must trace to the stated goal. List anything
you chose not to touch.
```

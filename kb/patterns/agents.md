---
id: "pat-001"
type: "pattern"
created: "2026-01-15"
updated: "2026-01-15"
status: "active"
tags:
  - "agents"
  - "sub-agents"
  - "context"
---

# Patterns: Agents

> Example file. Illustrative patterns; replace with your own.

## Spawn sub-agents only with a written contract

**Pattern:** when an agent spawns a sub-agent, pass an explicit work order
(goal, inputs, done-when) instead of dumping the parent's context.

**Why it works:** sub-agents start cold. A one-paragraph contract is cheaper than
re-deriving context and keeps token spend bounded and the task scoped.

**How to apply:**

- Template the work order: `Goal / Inputs / Done when`.
- Require the sub-agent to return only the result and changed files.

**Anti-pattern:** forwarding the whole parent transcript "so it has context" —
this inflates cost and blurs the task.

**References:** see `digests/example-digest.md`.

## Cache-stable file ordering cuts re-read cost

**Pattern:** keep the agent's read order of canonical files stable across runs.

**Why it works:** stable ordering keeps the prompt cache warm; reordering forces
uncached re-reads of the same content.

**How to apply:** fix a canonical read order (`MAP.md`) and follow it every run.

**References:** [[evals]] for how to measure the token ratio.

---
id: "wf-002"
type: "workflow"
created: "2026-01-17"
updated: "2026-01-17"
status: "active"
tags:
  - "intake"
  - "routing"
---

# Workflow: Promote an Insight into the KB

> Example file. Replace with your own.

## Goal

Turn a raw finding (from a digest or manual intake) into a durable, well-placed
KB entry.

## When to use

Any time a finding clears the intake bar (novelty, actionability, transferability,
durability, strength).

## Steps

1. Classify the insight (pattern / workflow / prompt / tool / project / business /
   reference) using `MAP.md`.
2. Search the target bucket for an existing home. Update it if found.
3. If no home exists, create a file from the matching `templates/template-*.md`.
4. Write a tight, claim-like entry — not a summary.
5. Cross-link related entries with `[[note]]`.
6. Verify by re-reading or searching the touched file.

## Rules

- One idea, one home. Cross-link instead of duplicating.
- Default to extraction. If it does not clear the bar, do not store it.

## References

- `workflows/implicit-intake.md`, `workflows/repo-intake.md`.

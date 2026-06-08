---
id: "wf-001"
type: "workflow"
created: "2026-01-17"
updated: "2026-01-17"
status: "active"
tags:
  - "review"
  - "maintenance"
---

# Workflow: Weekly KB Review

> Example file. Replace with your own.

## Goal

A KB that stays small, consistent, and high-signal as the daily digest feeds it.

## When to use

Once a week, after ~5-7 digest runs have promoted new entries.

## Steps

1. Read the last 7 rows of `digests/runs.md`.
2. Open each `kb/` file touched that week.
3. Merge near-duplicate entries; keep the stronger framing.
4. Demote stale tool/news entries to `status: watching` or `dropped`.
5. Check every new file follows its `templates/template-*.md`.

## Rules

- Consolidate before you create. Prefer fewer, denser files.
- Cross-link related entries with `[[note]]` instead of duplicating.

## References

- [[new-entry]] for how entries enter in the first place.

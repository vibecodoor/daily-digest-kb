---
id: "pat-002"
type: "pattern"
created: "2026-01-16"
updated: "2026-01-16"
status: "active"
tags:
  - "evals"
  - "measurement"
---

# Patterns: Evals

> Example file. Illustrative patterns; replace with your own.

## Report eval variance, not just the mean

**Pattern:** run each eval case 3-5 times and report the spread, not a single score.

**Why it works:** one score hides flakiness. Small prompt changes often land
inside the noise band and look like wins when they are not.

**How to apply:**

- Repeat each case N times; report median + min-max range.
- Only call a change a win if its median clears the previous range.

**Anti-pattern:** comparing two single-run scores and shipping the "better" prompt.

**References:** see `digests/example-digest.md`.

## Weak-findings days store nothing

**Pattern:** when a digest run surfaces nothing durable, store nothing and say so.

**Why it works:** padding the KB with evergreen advice degrades retrieval quality
for everything else.

**How to apply:** allow an empty KB-update section; only the run note is required.

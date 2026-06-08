---
name: daily-digest
description: Run the daily AI edge digest for this knowledge base. Use when the user says "run the daily digest", "daily digest", "today's digest", or wants to scout fresh AI/vibe-coding sources and update the KB. Reads the digest workflow, scouts sources, writes a dated digest to digests/, and promotes durable insights into kb/.
---

# Daily Digest — Launcher

Thin launcher for the daily digest. The full specification (sources, protocol,
output shape) lives in [`workflows/daily-ai-digest.md`](../../workflows/daily-ai-digest.md).
This skill does not duplicate it — it runs it.

## When to use

- The user asks to run the daily digest, build today's digest, or scout fresh AI
  edge.
- A scheduled routine / cron invokes the daily run.

## Run protocol

1. Read [`INSTRUCTIONS.md`](../../INSTRUCTIONS.md).
2. Read [`workflows/daily-ai-digest.md`](../../workflows/daily-ai-digest.md) in full —
   it is the source of truth for sources, tiers, freshness, and anti-repeat rules.
3. Read the last ~10 rows of [`digests/runs.md`](../../digests/runs.md) for
   anti-repeat context.
4. Read [`workflows/implicit-intake.md`](../../workflows/implicit-intake.md) and
   [`workflows/repo-intake.md`](../../workflows/repo-intake.md) so KB promotion
   follows the intake rules.
5. Execute the **Daily Run Protocol** from the workflow:
   - check every source across all four tiers (the mandatory floor), then search
     broadly beyond the list;
   - cluster signals, apply the evidence gate, filter hard for durable edge.
6. Produce the digest in the shape from
   [`templates/template-digest.md`](../../templates/template-digest.md) and
   deliver it to the user. Do not archive it per-day by default — archiving the
   full text to `digests/` is optional.
7. Promote only durable, non-duplicate insights into `kb/`, routing via
   [`MAP.md`](../../MAP.md) and shaping each entry with the matching
   `templates/template-*.md`.
8. Append one row to [`digests/runs.md`](../../digests/runs.md), ending with the
   mandatory `Coverage:` line.
9. Verify KB edits by re-reading or searching the touched files.

## Output

- The digest, delivered to the user (optionally archived under `digests/`).
- One new row in `digests/runs.md` (the persistent record).
- 0-N updated `kb/` files (only durable, non-duplicate insights).

## Guardrails

- Never invent releases, dates, benchmarks, pricing, funding, stars, or features.
- Never dump raw digest text into `kb/` — `kb/` holds only the distillate. The
  persistent run record is `digests/runs.md`.
- A run is incomplete without a filled coverage ledger and a `Coverage:` line.
- If fresh findings are weak, say so — do not pad with evergreen advice.

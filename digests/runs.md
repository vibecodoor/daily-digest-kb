# Daily Digest — Run Notes

Append-only log, one row per run. Kept separate from the workflow file so the
engine stays small and stable.

- Append one row per run (newest at the bottom).
- For anti-repeat checks during a new run, read the last ~10 rows.
- Older rows are archival only.
- The `Strongest new signals` cell **must** end with a `Coverage:` line. A row
  without one marks an incomplete run.

| Date | Strongest new signals | KB files updated | Do not repeat soon unless changed |
|---|---|---|---|
| 2026-01-15 | Sub-agent work-order contract; cache-stable file ordering. Coverage: T1 5/5, T2 6/6, T3 5/6, T4 3/3; skips: reddit: no API | `kb/patterns/agents.md`, `kb/prompts/agents.md` | sub-agent contract; cache ordering |
| 2026-01-16 | Report eval variance not mean; weak-day = store nothing. Coverage: T1 5/5, T2 5/6, T3 6/6, T4 3/3; skips: ossinsight: timeout | `kb/patterns/evals.md` | eval variance practice |

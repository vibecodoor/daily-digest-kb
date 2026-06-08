# AI Digest — example output

> **Sample only.** This shows the *shape* of a digest run. By default a digest is
> **delivered to you** (terminal, chat, Telegram — wherever you read it) and is
> **not archived per-day**. What persists is the run row in
> [`runs.md`](./runs.md) plus any durable insights promoted into `kb/`.
> Keeping full-text archives here is optional — see `workflows/daily-ai-digest.md`.
>
> All items below are illustrative, not real claims.

## 1. Top news of the day

- **Example coding agent ships sub-agent spawning** — a CLI agent adds scoped
  sub-agents with their own context window. ([source](https://example.com/changelog))
- **Eval harness adds variance reporting** — an eval tool now reports run-to-run
  variance, not just a single score. ([source](https://example.com/eval))

## 2. Top edge observations

### Spawn sub-agents only with a written contract

- **What:** pass an explicit work order (goal, inputs, done-when) instead of
  dumping the parent context.
- **Why it matters:** sub-agents start cold; a contract beats re-deriving context
  and bounds token cost.
- **How to apply:** template the work order; require `goal / inputs / done-when`.
- **Proof gate:** compare token spend and success with vs without the contract on
  5 real tasks.

### Report eval variance, not just the mean

- **What:** run each eval case 3-5 times; report the spread, not one score.
- **Why it matters:** a single score hides flakiness; small prompt changes hide
  inside the noise band.
- **How to apply:** repeat each case N times; report median + range; only accept a
  change that clears the band.
- **Proof gate:** re-run a known-flaky case 5× and show the range.

## 3. Ready-to-use workflows / prompts / techniques

```text
Spawn a sub-agent with this contract:
- Goal: <one verifiable outcome>
- Inputs: <files / data it may read>
- Done when: <explicit completion test>
Return only the result and the files you changed.
```

## Useful GitHub repositories

- **example/mcp-gateway** — route many MCP servers behind one endpoint; useful
  when an agent juggles 5+ connectors. ([repo](https://github.com/example/mcp-gateway))

## What to take away today

- Add a sub-agent work-order template to `kb/prompts/`.
- Add a variance-first eval note to `kb/patterns/`.
- Try `example/mcp-gateway` if you run multiple MCP servers.

## KB updates

- **Files changed:** `kb/patterns/agents.md`, `kb/patterns/evals.md`, `kb/prompts/agents.md`
- **Insights added:** sub-agent contract; eval variance practice; sub-agent work-order prompt.
- **Intentionally skipped:** the eval-tool release itself (ephemeral — the durable
  lesson is the practice, not the version).
- **Verification:** re-read the touched files after edit.

<!-- Run-ledger line: Coverage: T1 5/5, T2 6/6, T3 5/6, T4 3/3; skips: reddit: no API -->

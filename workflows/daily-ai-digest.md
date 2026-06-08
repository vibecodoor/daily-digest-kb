# Workflow: Daily AI Edge Digest

Use this file as the persistent context surface for the daily AI / vibe-coding
digest automation.

> **Adapting to another domain:** this file is the single point of
> customization. Rewrite `Research Focus` and `Durable Alpha Sources` to your
> topic and the rest of the machine works unchanged.

## Purpose

Produce a fresh digest about practical AI edge, then update the KB with only
durable, useful insights.

This is not a generic AI news workflow. The main job is scouting: find new
useful tricks, patterns, workflows, repos, tools, prompts, and product ideas
around AI-assisted building. News is secondary context.

## Read Order

Every automation run must read:

1. `INSTRUCTIONS.md`
2. `workflows/daily-ai-digest.md`
3. `workflows/implicit-intake.md`
4. `workflows/repo-intake.md` if GitHub repositories are found

Then search the smallest relevant KB surfaces (via `MAP.md`) before opening files.

## Research Focus

- vibe coding
- Codex, Claude Code, Cursor, Gemini CLI
- AI agents and agent workflows
- MCP, RAG, evals, guardrails
- token saving and context engineering
- GitHub tooling and open-source AI repos
- agent orchestration and automation
- research workflows
- solo-builder product development
- monetizable AI/product ideas

## Durable Alpha Sources

These are a mandatory **floor**, not a ceiling. Every run must check all sources
across all four tiers. The run must not stop here either: broad search beyond
this list is also required, and a run is incomplete if it relies on the list
alone. The list is a safety net so that nothing important is silently missed;
novelty still comes from going wider.

Tiers indicate signal density and how to weight findings, not whether to check
the source.

### Tier 1 — primary changelogs

- Claude Code: https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md
- Codex CLI: https://developers.openai.com/codex/changelog
- Cursor: https://cursor.com/changelog
- Gemini CLI: https://geminicli.com/docs/changelogs/
- GitHub Copilot CLI: https://github.blog/changelog/label/copilot/

### Tier 2 — ecosystem and trend signals

- GitHub Trending (last 24h and weekly): https://github.com/trending
- OSSInsight AI trending: https://ossinsight.io/trending/ai
- Trendshift daily: https://trendshift.io/
- Claude Code marketplaces: https://claudemarketplaces.com/
- Anthropic releasebot: https://releasebot.io/updates/anthropic
- OpenAI releasebot: https://releasebot.io/updates/openai

### Tier 3 — high-signal communities and writers

- Hacker News front page filtered for `ai|agent|mcp|claude|codex|cursor`
- r/ClaudeAI, r/LocalLLaMA, r/cursor (top of week)
- Simon Willison: https://simonwillison.net/
- Addy Osmani: https://addyosmani.com/blog/
- LangChain blog: https://blog.langchain.com/
- arxiv cs.AI new + cs.SE new (filter for agent/context/eval titles)

### Tier 4 — security and supply-chain

- Anthropic and OpenAI security advisories
- thehackernews.com tag for MCP / AI agent
- agent-security-scanner-mcp issues and releases

### Anti-noise rules

- Skip "ultimate list 2026" SEO posts and generic listicles unless they
  reference a concrete unseen repo or workflow.
- Skip vendor marketing posts unless they document a new mechanism.
- A source that appears 3 runs in a row without yielding a durable insight gets
  downgraded one tier.

## Scouting Style

Start broad, then filter. Do not let the workflow become too narrow because of
prior run notes.

Look especially for:

- new or trending GitHub repositories;
- small practical tools, scripts, MCP servers, skills, plugins, templates, CLIs;
- concrete agent/coding workflows people are actually using;
- new prompt patterns, context-engineering tricks, token-saving tactics, evals;
- useful research papers or benchmarks that can become a workflow;
- product-development insights for solo builders and AI-powered products;
- underrated hacks from changelogs, issues, release notes, demos, videos, and
  technical blog posts.

Prefer useful and surprising over perfectly comprehensive.

Radar lens:

- Score every candidate against your current projects, bottlenecks, and
  recurring workflows, not against generic AI-news importance.
- Look for signal clusters across unrelated sources: a changelog, repo, paper,
  thread, and security post pointing to the same workflow shift is usually
  stronger than one loud announcement.
- Prefer items that can feed an action surface today: a digest takeaway, a KB
  pattern, a reusable prompt/checklist, a repo/tool to test, or a product idea.
- For each serious finding, name the proof artifact that would make it
  trustworthy: benchmark, reproducible command, test output, screenshot/video,
  PR, eval result, trace, or source diff. If there is no plausible proof
  artifact, treat it as opinion or market context.
- Prefer "gotchas and landmines" over comprehensive documentation dumps. The
  edge is in the few constraints, failure modes, version quirks, and non-obvious
  checks that make agents fail.
- Treat accumulated source knowledge as time-sensitive: stale facts lose weight
  unless a new source revalidates them.
- Prefer official APIs, RSS, public changelogs, public docs, and allowed
  crawling; do not rely on restriction-bypass scraping as a normal workflow.

## Daily Run Protocol

1. Check every source across all four tiers in `Durable Alpha Sources` — all
   tiers are mandatory. Then — also required — search broadly for fresh sources
   and high-signal discoveries outside the list.
2. Verify factual claims that will be included as facts.
3. Compare recent run notes only to avoid stale repetition, not to suppress good
   discoveries.
4. Cluster related signals and decide what each surviving item should do: inform
   the news context, become an edge finding, become a ready
   workflow/prompt/checklist, enter a try-today action, update the KB, or be
   intentionally skipped.
5. For each promoted edge finding, include a practical evidence gate: what to
   run, inspect, measure, screenshot, diff, or evaluate before trusting it.
6. Deliver the digest to the user using the output shape below. The persistent
   record is the run-ledger row (step 9) plus the KB updates — archiving the full
   digest text to `digests/` is optional, not the default.
7. Extract only durable insights.
8. Update canonical KB files (route via `MAP.md`, shape via `templates/`) if the
   insight is strong and non-duplicate.
9. Append one short row to [../digests/runs.md](../digests/runs.md).
10. Verify KB edits by reading or searching the touched files.

## Source Coverage Ledger (mandatory)

A run is **incomplete** until this ledger is filled and a `Coverage:` line is
appended to the run-note row. For every source in all four tiers, mark `hit`
(the actual source URL was fetched this run) or `skip: <reason>`. A broad
web-search does **not** count as a `hit` for a listed source. Stopping early
because "enough strong findings" were already found is **not** a valid skip
reason; the floor is checked regardless.

- Tier 1: claude-code · codex · cursor · gemini-cli · copilot-cli
- Tier 2: gh-trending · ossinsight · trendshift · claudemarketplaces · releasebot-anthropic · releasebot-openai
- Tier 3: HN · reddit(ClaudeAI/LocalLLaMA/cursor) · simonwillison · addyosmani · langchain · arxiv(cs.AI+cs.SE)
- Tier 4: anthropic/openai-advisories · thehackernews(MCP/agent) · agent-security-scanner-mcp

Then broad search beyond the list (still required). Record the result as a
one-line coverage summary in the run note:
`Coverage: T1 x/5, T2 x/6, T3 x/6, T4 x/3; skips: <source: reason>`.

## Freshness Rules

- News: prefer the last 24-72 hours.
- Repos/tools/workflows: prefer the last 7-14 days when possible.
- Older items are allowed when trending, newly discovered, or newly useful.
- If strong findings are weak, say so instead of filling the digest with
  evergreen advice.
- Never invent releases, dates, benchmark claims, pricing, funding, repo
  features, or stars.

## Anti-Repeat Rules

Do not copy old digest content. Repeating a topic is allowed if the angle is
concrete and useful.

Avoid repeating a tool, repo, workflow, or conclusion from recent run notes
unless at least one is true:

- there is a new release or changelog item;
- there is a new practical use case;
- the KB needs a stronger framing;
- the item is used only as context for a new pattern.

Avoid repeating these evergreen points unless there is a new concrete angle:

- use `AGENTS.md` / `CLAUDE.md`; minimal diff; single-agent-first; context diet;
  terminal agents are useful; add evals; use MCP carefully; save state outside chat.

## KB Update Rules

Store only durable, concise, English KB entries. Route via `MAP.md`.

Default routing:

- named useful tool or repo → `kb/tools/catalog.md`
- reusable workflow or operating pattern → best `kb/patterns/*.md` or `kb/workflows/*.md`
- MCP ecosystem or connector lesson → `kb/tools/catalog.md`
- plugin/skill packaging lesson → `kb/tools/catalog.md` or `kb/patterns/*.md`
- market/product signal → `kb/business/*.md`
- reusable prompt → best `kb/prompts/*.md`

Do not store:

- raw digest text (that is what `digests/` is for);
- generic summaries;
- broad source/documentation dumps when a compact gotcha note would do;
- weak repos; repeated items;
- ephemeral pricing or rollout details unless they materially affect decisions.

## Digest Output Shape

Produce the digest in this shape (see `templates/template-digest.md`) and deliver
it to the user. The digest is **not** stored per-day by default — the persistent
record is the `digests/runs.md` row plus the KB updates. Archiving the full text
to `digests/` is optional.

```md
# AI Digest — YYYY-MM-DD

## 1. Top news of the day

3-5 compact verified items with links.

## 2. Top edge observations

3-6 practical patterns with: what it is; why it matters; how to apply it; who it
helps; the exact workflow/prompt/tool/approach.

## 3. Ready-to-use workflows / prompts / techniques

Copy-paste-ready prompts, checks, commands, or runbooks.

## Useful GitHub repositories

Only if strong repos were found.

## What to take away today

3-5 concrete actions.

## KB updates

- files changed; insights added; intentionally skipped items;
- verification performed by reading or searching touched files.
```

## Simplified Automation Prompt

Use this prompt when configuring the recurring automation (routine / cron):

```text
Read INSTRUCTIONS.md and workflows/daily-ai-digest.md, then create today's AI
edge digest.

This is not a generic AI news newsletter. The main goal is to find practical
edge for AI-assisted building: vibe coding; Codex, Claude Code, Cursor, Gemini
CLI; AI agents, MCP, RAG, evals, guardrails; context engineering and token
saving; trending or newly useful GitHub repos; small tools, skills, plugins,
templates, CLIs; new workflows, prompts, hacks, patterns, and product ideas for
solo builders.

Start broad. Search fresh sources, trending repos, changelogs, release notes,
papers, demos, technical posts, and high-signal community discussions.

Then filter hard:
- keep only things usable as an advantage;
- score against current projects, bottlenecks, and recurring workflows;
- look for clusters across sources pointing to the same practical shift;
- prefer concrete workflows over generic advice;
- prefer gotchas, landmines, failure modes, and proof gates over docs dumps;
- turn surviving items into an action surface;
- include what would prove the finding in practice;
- include source links for factual claims;
- do not invent facts, dates, features, stars, releases, or benchmarks;
- if fresh findings are weak, say so honestly.

Produce and deliver the digest. Then update the KB only with durable
non-duplicate insights (route via MAP.md, shape via templates/) and append a
short run note to digests/runs.md. The digest is not archived per-day by default;
the run note plus KB updates are the persistent record.
```

## Run Notes

Run history lives in [../digests/runs.md](../digests/runs.md) — kept separate so
this workflow file stays small and stable.

- Append one row per run to that file.
- For anti-repeat checks during a new run, read the last ~10 rows of that file.
- Older rows are archival only.

Schema (for reference; do not append rows here):

| Date | Strongest new signals | KB files updated | Do not repeat soon unless changed |
|---|---|---|---|

The `Strongest new signals` cell must end with a mandatory `Coverage:` line
(see `Source Coverage Ledger`). A row without a `Coverage:` line marks an
incomplete run.

## Candidate Backlog

Use this section only for ideas worth checking later. Keep it short.

| Added | Candidate | Why check later |
|---|---|---|
| | | |

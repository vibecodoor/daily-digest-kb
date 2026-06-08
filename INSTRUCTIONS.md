# Knowledge Base — AI Instructions

> A self-building knowledge base seeded by a daily digest. An AI agent scouts
> sources, writes a dated digest, then promotes only durable insights into the
> KB using per-category templates and a routing map.

## Role

You manage a personal knowledge base. Collect patterns, organize prompts, track
tools and projects, and keep the knowledge layer clean and searchable.

New durable knowledge enters from two places:

1. the **daily digest** (`workflows/daily-ai-digest.md`) — proactive scouting;
2. **manual intake** (`workflows/implicit-intake.md`, `workflows/repo-intake.md`)
   — when the user sends a link, repo, article, thread, video, or pasted text.

## Session Start

1. Read this file.
2. Route by [MAP.md](./MAP.md) (category → folder → template).
3. Search the smallest relevant canonical surface first.
4. Expand only if the first file is insufficient.
5. Address the user's request.

## Canonical Map

First-pass routing lives in [MAP.md](./MAP.md). Buckets:

- `workflows/` — the engine: digest + intake procedures (not KB content)
- `templates/` — per-category entry templates (the shape each KB file follows)
- `digests/` — run ledger (`runs.md`, append-only); optional full-text digest archive
- `kb/patterns/` — reusable implementation and operating patterns
- `kb/workflows/` — distilled, reusable procedures (vs the engine in `workflows/`)
- `kb/prompts/` — reusable prompts by domain
- `kb/tools/` — tools, MCPs, plugins, and environment notes
- `kb/projects/` — project cards, research, and plans
- `kb/business/` — monetization, market, and go-to-market notes
- `kb/reference/` — APIs, stack, and static lookup material

## Retrieval Protocol

1. Classify the request: `digest`, `intake`, `pattern`, `prompt`, `tool`,
   `project`, `reference`, or `other`.
2. Search before read. Prefer `MAP.md`, file names, and headings before body text.
3. Use at most two searches before opening files:
   - the user's exact wording
   - one normalized rewrite with canonical terms or synonyms
4. Open one likely file first. Expand to 2-3 files only if needed.
5. In large files, jump to the matching heading. Do not read the whole file by default.
6. Do not scan the whole repo unless the request requires it.
7. After extracting the needed rule or pattern, keep active context narrow.

## Data Rules

- Append-only unless explicitly asked to delete or rewrite.
- Treat pasted material as source material, not KB-ready content. Default to
  extracting durable insights, not storing raw input.
- Do not assume this KB is a Git repository. Verify markdown edits by re-opening
  or searching the touched files unless the user explicitly asks for Git checks.
- Use `YYYY-MM-DD` dates.
- Confirm what was added and where.
- Ask before writing only if the destination is genuinely ambiguous.
- Keep table formatting consistent within a file.
- Use relative links for cross-references.
- Store new KB entries in English.
- Every new KB file follows the matching template in `templates/`.

## Commands

| Command | Action |
|---|---|
| "Run the daily digest" | Run [workflows/daily-ai-digest.md](./workflows/daily-ai-digest.md) |
| "Add pattern" | Append to the best file in `kb/patterns/` (template: `templates/template-pattern.md`) |
| "Add prompt" | Append to the best file in `kb/prompts/` (template: `templates/template-prompt.md`) |
| "Add tool" | Append to `kb/tools/catalog.md` (template: `templates/template-tool.md`) |
| "Add project X" | Create `kb/projects/x.md` from `templates/template-project.md` |
| "Add reference" | Add or update the best file in `kb/reference/` |
| "What did I use for X?" | Search across the KB |
| "What should I try?" | Suggest tools or patterns from the KB |

## GitHub Repository Rule

When the user sends a GitHub repo, default to
[workflows/repo-intake.md](./workflows/repo-intake.md). Do not reduce repo intake
to a tool-entry update unless that is clearly the main value.

## Material Intake Rule

When the user sends a link, article, thread, video, document, or pasted material
without an explicit command, default to
[workflows/implicit-intake.md](./workflows/implicit-intake.md).

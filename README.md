# Daily Digest KB

> A knowledge base that gives you an edge — built from a daily digest.

A markdown-native template where an AI agent runs a **daily digest** and uses it
to **build a knowledge base around itself**. The agent scouts sources, writes a
dated digest, then promotes only durable insights into a structured KB using
per-category templates and a routing map.

No database. No backend. No scripts required. The whole thing is markdown +
instructions an AI coding agent (Claude Code, Codex, Cursor, Gemini CLI, …)
reads and acts on.

> Out of the box it ships configured for an **AI / vibe-coding edge digest**
> (tracking Claude Code, Codex, Cursor, MCP, agents, GitHub repos, etc.). The
> source list and research focus live inside `workflows/daily-ai-digest.md` —
> edit that one file to point the same machine at any domain.

## How it works

```
 daily run                deliver + log               grow
┌──────────┐   ┌─────────────────────┐   ┌──────────────────────┐
│ workflows│ → │ digest delivered to │ → │ kb/<bucket>/<entry>  │
│ (engine) │   │ you · row → runs.md │   │ (durable knowledge)  │
└──────────┘   └─────────────────────┘   └──────────────────────┘
                  ledger = the trail        routed via MAP.md
                  (archive optional)        shaped by templates/
```

1. **Engine** (`workflows/`) — the digest scouts sources; intake workflows
   absorb links/repos you hand it.
2. **Ledger** (`digests/`) — the digest is delivered to you; every run appends a
   row to `runs.md`. That row plus the KB updates are the persistent record.
   Archiving the full digest text per-day is optional.
3. **Knowledge** (`kb/`) — only durable, reusable insights get promoted here,
   routed by `MAP.md` and shaped by `templates/`.

## Folder structure

```
.
├── INSTRUCTIONS.md     # how the agent operates: read-order, routing, rules (source of truth)
├── CLAUDE.md           # thin auto-load pointer → INSTRUCTIONS.md (Claude Code)
├── AGENTS.md           # thin auto-load pointer → INSTRUCTIONS.md (Codex, Cursor, Gemini CLI, …)
├── MAP.md              # routing map: category → kb folder → template
├── workflows/          # the engine (not KB content)
│   ├── daily-ai-digest.md   # the digest spec: sources, protocol, output shape
│   ├── implicit-intake.md   # absorb a link/article/thread/video/paste
│   └── repo-intake.md       # absorb a GitHub repo
├── skills/
│   └── daily-digest/        # one-command launcher for the digest
│       └── SKILL.md
├── templates/          # per-category entry templates (the shape of each KB file)
├── digests/            # runs.md ledger (append-only) + optional digest archive
└── kb/                 # the growing knowledge base
    ├── patterns/  workflows/  prompts/
    ├── tools/     projects/   business/   reference/
```

## Quick start

You need an AI coding agent with file access (Claude Code, Codex CLI, Cursor,
Gemini CLI, etc.).

**Get the template** — use GitHub's *Use this template* button, or:

```bash
npx degit vibecodoor/daily-digest-kb my-digest-kb
cd my-digest-kb
```

**Point it at your agent.** Open the folder as your project. `CLAUDE.md`
(Claude Code) and `AGENTS.md` (Codex, Cursor, Gemini CLI, …) auto-load on session
start and point the agent to `INSTRUCTIONS.md` — it knows the rest.

**(Optional) Adapt the topic.** Edit `workflows/daily-ai-digest.md` →
`Research Focus` and `Durable Alpha Sources` to your domain. Leave it as-is to
run the AI / vibe-coding digest.

## Running the daily digest — three ways

Pick whichever fits how you work. All three drive the same engine.

### 1. As a skill (one command)

The repo ships a launcher skill at `skills/daily-digest/`. Make it available to
your agent (for Claude Code, copy or symlink it into `.claude/skills/`, or load
the repo as a plugin), then:

```
/daily-digest
```

or just tell the agent: **"run the daily digest"**. It reads the workflow, scouts
sources, delivers today's digest, logs a row to `digests/runs.md`, and promotes
durable insights into `kb/`.

### 2. As a routine / scheduled automation (hands-off, daily)

Let the agent run it for you every day.

- **Claude Code** — schedule a routine with the prompt below (see
  `workflows/daily-ai-digest.md` → *Simplified Automation Prompt*).
- **Codex** — create a scheduled automation / cron task with the same prompt.

```text
Read INSTRUCTIONS.md and workflows/daily-ai-digest.md, then create today's
digest. Scout the listed sources plus fresh discoveries, filter hard for
durable edge, deliver the digest, promote only durable non-duplicate insights
into kb/ using MAP.md and templates/, and append one row to digests/runs.md.
```

A typical cron is once per morning. The run is self-contained — it records the
run in `runs.md` and commits any KB updates as plain markdown.

### 3. Manually (through the KB itself)

Open the project and paste the *Simplified Automation Prompt* from
`workflows/daily-ai-digest.md` into your agent. Same result, run on demand.
This is also how you do ad-hoc intake: just send the agent a link or a repo and
it follows `implicit-intake.md` / `repo-intake.md`.

## Adapting it to your own data

- **Change the domain** → edit `Research Focus` + `Durable Alpha Sources` in
  `workflows/daily-ai-digest.md`.
- **Change the KB shape** → edit `MAP.md` (buckets) and the matching
  `templates/template-*.md`.
- **Seed examples** → every `kb/<bucket>/` ships a `README.md` + 2 example
  entries showing the format. Replace them with your own.

## Design notes

- **Markdown is the database.** Everything is human-readable and diff-friendly.
- **Provenance is separate from knowledge.** The digest is delivered to you and
  logged as a row in `digests/runs.md`; `kb/` holds only the curated distillate.
  The agent never dumps raw digest text into the KB.
- **Templates drive growth.** New knowledge always takes the shape its template
  defines, so the KB stays consistent as it scales.
- **Extraction over storage.** The default is to distill 1-3 durable bullets,
  not to hoard raw input.

## Contributing

Issues and PRs welcome — especially new source tiers, template improvements, and
domain config examples. Keep KB entries in English and follow the templates.

## License

[MIT](./LICENSE).

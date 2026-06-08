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
│   └── daily-digest/        # portable SKILL.md launcher — works with any agent
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

**1. Get the template** — pick one:

```bash
# A) GitHub "Use this template" button → creates your own repo (no terminal)

# B) copy the files without git history (needs Node):
npx degit vibecodoor/daily-digest-kb my-digest-kb

# C) plain clone, no Node required:
git clone https://github.com/vibecodoor/daily-digest-kb.git my-digest-kb
```

Then `cd my-digest-kb`.

**2. Open it in your agent.** Open the folder as your project. `CLAUDE.md`
(Claude Code) and `AGENTS.md` (Codex, Cursor, Gemini CLI, …) auto-load on session
start and point the agent to `INSTRUCTIONS.md` — it knows the rest. Nothing else
to install.

**3. Or just tell your agent** — paste this on the first message:

```text
This project is an AI-operated knowledge base. Read INSTRUCTIONS.md and follow it.
To produce today's digest, follow workflows/daily-ai-digest.md.
```

**(Optional) Adapt the topic.** Edit `workflows/daily-ai-digest.md` →
`Research Focus` and `Durable Alpha Sources` to your domain. Leave it as-is to
run the AI / vibe-coding digest.

## Running the daily digest — three ways

Pick whichever fits how you work. All three drive the same engine.

### 1. As a skill

The repo ships a portable launcher at `skills/daily-digest/SKILL.md` — a standard
`SKILL.md` that **any agent** (Claude Code, Codex, Cursor, Gemini CLI, …) can read
and run. Just tell your agent **"run the daily digest"** and it follows the skill:
scouts sources, delivers today's digest, logs a row to `digests/runs.md`, and
promotes durable insights into `kb/`.

The skill ships *inside* the repo and operates on its own workflow files, so it's
**not** installed via `npx` or a registry — it travels with the template.

**Optional — Claude Code slash command.** For a `/daily-digest` shortcut, copy the
skill into Claude Code's project-skill folder once (other agents don't need this):

```bash
mkdir -p .claude/skills && cp -r skills/daily-digest .claude/skills/   # Windows: just copy the folder
```

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

## Using it as a knowledge base

The daily digest is only *one* way knowledge gets in. The other is **you** — hand
the agent anything and it files the durable parts for you. It distills, it
doesn't hoard: every input is scored, the reusable signal is extracted, and it's
routed into the right `kb/` bucket (via `MAP.md`, shaped by `templates/`).

**Drop in material.** Send the agent a link, article, thread, video, or pasted
notes — no command needed. It follows `workflows/implicit-intake.md`: scores the
material, keeps only what's durable, and updates the best existing note (or
creates one). Hand it a GitHub repo instead and it switches to
`workflows/repo-intake.md`, mining architecture, workflows, and gotchas.

Just say things like:

```text
Save what's useful from this: <link or pasted text>
Study this repo and add what's worth stealing: <github url>
Add a pattern: <your rule of thumb>          → files into kb/patterns/
Add this prompt: <prompt>                     → files into kb/prompts/
Add a tool: <name> — <what it does>           → files into kb/tools/catalog.md
Add project <name>                            → new card in kb/projects/
```

**Pull it back out.** Ask the KB like a second brain:

```text
What did I save about MCP?
What should I try for evals?
What patterns do I have on context engineering?
```

It searches the canonical surfaces first (via `MAP.md`), so retrieval stays cheap
as the KB grows. Full command list lives in `INSTRUCTIONS.md`.

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

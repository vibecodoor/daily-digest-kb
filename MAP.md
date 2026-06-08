# MAP — Routing Map

First-pass routing for everything in this knowledge base. Read this after
`INSTRUCTIONS.md` and before opening file bodies. It answers one question:
**given a piece of knowledge, which folder does it go in and which template
defines its shape?**

## Layers

| Layer | Folder | What lives here |
|---|---|---|
| Engine | `workflows/` | The digest + intake procedures that *produce* knowledge. Not KB content. |
| Templates | `templates/` | The shape of each KB entry type. Every new KB file starts from one. |
| Ledger | `digests/` | `runs.md` — the append-only run record (one row per run). The digest itself is delivered to you, not archived per-day; full-text archiving here is optional. |
| Knowledge | `kb/` | Distilled, durable, reusable knowledge. The thing that grows. |

## Routing table

| Category | Folder | Template |
|---|---|---|
| Reusable pattern / anti-pattern / heuristic | `kb/patterns/` | `templates/template-pattern.md` |
| Repeatable procedure or operating flow | `kb/workflows/` | `templates/template-workflow.md` |
| Reusable prompt | `kb/prompts/` | `templates/template-prompt.md` |
| Tool / MCP / plugin / environment note | `kb/tools/` | `templates/template-tool.md` |
| Project card, plan, or research | `kb/projects/` | `templates/template-project.md` |
| Market / monetization / go-to-market note | `kb/business/` | `templates/template-business.md` |
| API / stack / static lookup reference | `kb/reference/` | `templates/template-reference.md` |
| A digest run (delivered; archive optional) | `digests/` | `templates/template-digest.md` |

## Routing rules

- **Default to extraction, not storage.** Most material yields 1-3 durable
  bullets, not a new file. Update an existing canonical file before creating one.
- **Smallest surface wins.** Route to the most specific existing file that fits.
- **One idea, one home.** Do not duplicate the same insight across files without
  a retrieval reason. Cross-link instead.
- **New file only when** the knowledge will be reused as its own stable retrieval
  surface and does not fit any existing destination.
- **Engine vs KB.** Procedures that *run* (scouting, intake) live in `workflows/`.
  Procedures you *reuse as knowledge* live in `kb/workflows/`.

## Value-density routing

- 1-3 strong reusable insights → add bullets/rows to the best existing canonical file.
- A new reusable pattern/workflow/prompt/tool → focused section in the right file.
- A dense cluster worth preserving together → a dedicated note, plus the distilled
  takeaway added to the canonical layer.
- Mostly recap, fluff, or duplicate → do not store.

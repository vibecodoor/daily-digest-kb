# Workflow: Repo Intake

Use this workflow when the user sends a GitHub repository link or asks to study
an open-source repo.

## Goal

Treat repositories as source material to distill into durable KB knowledge before
treating them as tool entries.

Prioritize:

- architecture and system boundaries
- skills, plugins, and extension systems
- orchestration and workflow patterns
- memory and context patterns
- security rails and permission boundaries
- deployment and runtime choices
- product UX patterns for agentic systems
- anti-patterns and limits worth not copying

## Default Workflow

1. Classify the repo
2. Inspect only the smallest relevant surface
3. Evaluate the repo material
4. Extract reusable ideas
5. De-duplicate against the KB
6. Route ideas into existing canonical files (via `MAP.md`)
7. Add a tool entry only if it adds separate value
8. Report what mattered, what was noise, and what was added

Default write behavior:

- after file-by-file inspection and destination choice, update the KB immediately
- do not stop to ask for confirmation unless the destination is genuinely
  ambiguous or the evidence is too weak
- keep the write scoped to the smallest canonical surface that fits

## Step 1 — Classify the Repo

Decide what kind of repo this is:

- product or app
- framework or runtime
- coding harness or orchestration layer
- memory provider, retrieval layer, or context engine
- plugin, skill, or integration pack
- reference implementation
- template or starter
- infrastructure or deployment tooling

The classification determines what matters most.

## Step 2 — Inspect the Smallest Relevant Surface

Start narrow. Prefer:

- `README` and docs landing pages
- project structure
- config and manifests
- deployment files
- security docs
- examples, templates, and sample agents
- extension or skill loading mechanisms

Study the repo file by file through the smallest relevant chain.

- Do not infer architecture or behavior from `README`, folder names, or filenames alone
- For any non-trivial claim, open the concrete source files that implement it
- Trace the minimal relevant path: entrypoint → config → core module → supporting file
- Expand one file at a time and stop when the claim is confirmed
- If you did not verify a claim in source, label it as an inference

Expand only if needed into:

- source folders that reveal architecture
- tests that show intended workflows
- scripts or CLI entrypoints

Avoid reading the whole repo unless the structure is unclear.

## Step 3 — Evaluate the Repo Material

Use the same intake criteria as [implicit-intake.md](./implicit-intake.md):

- `novelty`: is this new to the KB or a materially better framing?
- `actionability`: can this change what the user builds, copies, or avoids?
- `transferability`: does it generalize beyond this specific repo?
- `durability`: will it still matter after the repo itself is forgotten?
- `strength`: is it a strong insight, heuristic, workflow, or implementation pattern?

If the repo yields mostly obvious structure, hype, or project-specific noise, do
not store much.

## Step 4 — Extract Reusable Knowledge

For each repo, ask:

### Architecture

- What are the main layers?
- How are agents, tools, memory, UI, runtime, and integrations separated?
- Is there a strong boundary between core runtime and extensions?

### Skills / Plugins / Extensions

- How are capabilities packaged, discovered, loaded, validated, permissioned?
- Is the extension model simple enough to reuse?

### Workflow / Orchestration

- Is it single-agent, multi-agent, scheduled, delegated, or long-running?
- What coordination pattern is worth stealing?

### Memory / Context

- How does it persist memory, logs, prompts, or state?
- What is always loaded vs fetched on demand?
- Are there token-economy lessons worth keeping?
- What owns source of truth: human-readable files, provider database, graph,
  event log, or derived index?

### Security / Ops

- What guardrails exist around tools, shell, files, secrets, auth, or plugin install?
- What boundaries should be copied as secure-by-default?

### Deployment / Runtime

- Local-first or cloud-first? Desktop, CLI, daemon, self-hosted, or chat-native?
- Which runtime choices are product value rather than implementation detail?

### Product Pattern

- What is the actual user-facing loop?
- What turns capability into usable product UX?

### Anti-Patterns / Limits

- Where is the repo overcomplicated, risky, vague, or too infra-heavy?
- What should not be copied?

Default to extraction, not storage:

- distill the strongest reusable lessons
- rewrite them into KB language
- avoid repo recap unless the recap itself is reusable
- keep product names only where the name has retrieval value

## Step 5 — Choose the Destination

Write to the smallest number of existing files that preserve the insight well.

Default rule:

- do not create a repo-specific note file for each GitHub repo
- first try to distribute the useful parts into existing canonical files
- create a new file only if the knowledge genuinely does not fit any current
  destination and will be reused as its own reference surface

Routing heuristic (see `MAP.md`):

- product name and short comparison value → `kb/tools/catalog.md`
- reusable operating lesson → `kb/patterns/*.md`
- plugin, skill, or MCP ecosystem lesson → `kb/tools/catalog.md`
- stack/runtime choice → `kb/reference/stack.md`
- business or monetization lesson → `kb/business/*.md`
- agent-team architecture → `kb/patterns/*.md`

Do not duplicate the same idea across multiple files without a retrieval reason.

Routing by value density:

- 1-3 strong reusable insights → update existing canonical files only
- a dense cluster that deserves to stay together → a dedicated note only if it
  will become a stable retrieval surface
- mostly useful as a named product reference → distilled lesson plus a short tool entry
- mostly noise or non-transferable detail → do not store it

## Step 6 — Tool Entry Rule

Add or update a tool entry only if at least one is true:

- the repo is directly useful to try or compare as a tool
- it is a recurring market reference worth tracking by name
- it has a distinct product surface beyond the extracted patterns

If the main value is architecture or workflow, store that first. Tool entries
stay short.

## Step 7 — Output Standard

When reporting back:

- summarize the reusable insight, not just the repo
- say how the repo scored on novelty, actionability, transferability, durability, strength
- say what was noise vs what was worth keeping
- confirm exactly what was added and where
- mention if you updated an existing entry instead of adding a duplicate

## Heuristic

Ask: `What can future projects steal from this repo?`

Not: `Should I add this to the tools list?`

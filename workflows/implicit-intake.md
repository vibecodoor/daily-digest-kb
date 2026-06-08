# Workflow: Implicit Intake

Use this workflow when the user sends a link, repo, article, thread, video,
document, or pasted text without an explicit command.

## Default Interpretation

Treat the input as:

1. material to analyze
2. a candidate source of durable knowledge
3. something that may update the KB if it is worth keeping
4. source material to distill, not something to store verbatim by default

## Core Workflow

1. Inspect the material
2. Score it for novelty, actionability, transferability, durability, and strength
3. Separate reusable signal from hype, recap, and generic summary
4. Check whether the KB already contains the same idea (search via `MAP.md`)
5. Promote only the strongest reusable insight into the KB
6. Confirm what was added, why it mattered, and where

Fast path:

- if the user gives an explicit destination and the update is narrow, read that
  owner, update/append there, and confirm
- do not run full scoring or reflection for obvious targeted writes
- if the destination becomes ambiguous, return to the core workflow

## Evaluation Criteria

- `novelty`: new to the KB or a materially better framing of an existing idea
- `actionability`: can change what the user does, builds, or decides
- `transferability`: reusable beyond the original source or one-off context
- `durability`: likely to remain useful after the source itself fades
- `strength`: strong insight, heuristic, workflow, prompt, or implementation detail

If the material scores low on most of these, do not store it.

## Promotion Rules

- Default to extraction, not storage
- Prefer updating an existing canonical file over creating a new file
- If the same owner/topic already exists, update or consolidate it before
  creating a new section/file
- Add only concise, self-contained statements that will still make sense later
- Rewrite source ideas into KB language; do not dump raw text unless the exact
  wording matters
- Keep titles and bullets searchable and claim-like
- New KB files follow the matching template in `templates/`

## Routing by Value Density

- If the material yields 1-3 strong reusable insights:
  add distilled bullets, rows, or short sections to the best existing canonical file
- If the material yields a new reusable pattern, workflow, prompt, or tool heuristic:
  add a focused section to the relevant canonical file (route via `MAP.md`)
- If the material contains a dense cluster of high-value insights that deserve
  preservation together: create a dedicated note and add only the distilled
  takeaway to the canonical layer
- If the material is mostly fluff, recap, or duplicate knowledge: do not store it

## Raw Source Storage

Store raw or lightly processed source material only if at least one is true:

- the source is unusually valuable and hard to reproduce
- the exact wording is likely to be reused directly
- the material has dense value but cannot be cleanly decomposed into a few
  distilled entries yet

If you store a source, still extract the main takeaways into the KB instead of
relying on the source note alone.

## Good Candidates for KB Updates

- reusable patterns and anti-patterns
- strong prompts and workflows
- tooling insights worth repeating
- implementation details with lasting value
- market or business insight that changes decisions

## Avoid Storing

- generic summaries
- marketing fluff
- obvious advice already covered elsewhere
- ephemeral metrics unless they materially affect evaluation
- raw material copied "just in case"
- source structure when only the distilled insight matters

## Ask Before Writing Only If

- the source could belong to multiple places with different meanings
- the user likely wants project-specific tracking instead of general KB capture
- the source is too unreliable to evaluate safely

## Special Rule for GitHub Repositories

Do not treat a repo as "just another tool" by default.

Start with [repo-intake.md](./repo-intake.md).

Apply the same evaluation criteria, promotion rules, and value-density routing
from this workflow, but use the repo-specific inspection and destination rules
from `repo-intake.md`.

Prioritize:

- architecture
- workflows
- memory/context patterns
- security rails
- deployment/runtime choices
- reusable product patterns

Add or update a tool entry only if the repo also matters as a named tool reference.

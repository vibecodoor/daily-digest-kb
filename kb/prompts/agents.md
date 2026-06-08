---
id: "prm-001"
type: "prompt"
created: "2026-01-15"
updated: "2026-01-15"
status: "active"
tags:
  - "agents"
  - "sub-agents"
---

# Prompts: Agents

> Example file. Replace with your own.

## Sub-agent work order

**Use case:** when spawning a scoped sub-agent (see [[agents]] pattern).

```text
Spawn a sub-agent with this contract:
- Goal: {{one verifiable outcome}}
- Inputs: {{files / data it may read}}
- Done when: {{explicit completion test}}
Return only the result and the files you changed.
```

**Notes:** keep the goal to one outcome; if you need two, spawn two sub-agents.

**References:** `digests/example-digest.md`.

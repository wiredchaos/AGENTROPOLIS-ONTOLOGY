# Karpathy Obsidian Wiki Adapter

Status: active infrastructure pattern

## Core lock

AGENTROPOLIS uses the AGENTROPOLIS ONTOLOGY and AGENTROPOLIS KNOWLEDGE GRAPH for infrastructure memory.

AKIRA CODEX is excluded from AGENTROPOLIS infrastructure and remains WIRED CHAOS lore only.

## Pattern

AGENTROPOLIS adopts the Karpathy Wiki Method as an Obsidian-compatible second-brain pattern.

This is not treated as a standalone app. It is treated as an operating pattern:

```text
Sources -> Obsidian wiki mirror -> agent query -> ontology write-back -> richer memory
```

## AGENTROPOLIS adaptation

The Obsidian layer is the human-readable wiki.

The ontology layer is the agent-readable source of truth.

AGENTROPOLIS should mirror durable notes, repo observations, build logs, prompt patterns, and operator decisions into structured ontology entities.

## Wiki page types

Recommended wiki pages:

- Project pages
- Repository pages
- Agent pages
- Workflow pages
- Prompt pages
- Decision pages
- Rule pages
- Risk pages
- Metric pages
- Operator log pages

## Write-back rule

Every useful note should become structured memory when it creates reusable knowledge.

Examples:

- A repeated instruction becomes a Rule entity.
- A build pattern becomes a Workflow entity.
- A product direction becomes a Decision entity.
- A useful prompt becomes a Prompt entity.
- A repo observation becomes a Repo Memory entity.

## Approval gate

Before agents change behavior or wire new recurring automations, the operator must approve the discovered connections.

Recommended flow:

```text
Read sources -> propose links -> operator approves -> update wiki -> update ontology -> test run -> schedule
```

## Repository role

This repository owns the canonical schema for how Obsidian wiki pages map into AGENTROPOLIS ontology entities and relationships.

# Compiled Knowledge Architecture

This document locks the AGENTROPOLIS ontology position on self-maintaining knowledge bases.

The core rule is simple:

```text
Do not treat knowledge as a pile of notes.
Treat knowledge as a compiled artifact with source evidence, entity links, validation checks, and receipts.
```

## Purpose

Most knowledge systems decay because maintenance is treated as a human chore.

AGENTROPOLIS uses the ontology as the compiled knowledge layer. Raw sources stay immutable. The model helps maintain summaries, entity pages, links, contradictions, indexes, and lint reports.

The human owns judgment.

The model owns bookkeeping.

The ontology owns structure.

Receipts prove what changed.

## Layer Model

```text
sources/
  Immutable inputs, records, documents, screenshots, transcripts, links, filings, datasets.

ontology/
  Entities, relationships, districts, agents, tools, skills, policies, workflows, permissions.

knowledge/
  Compiled pages, summaries, decision records, doctrine, canon notes, operational context.

indexes/
  Navigation maps that let agents find the right pages without brute-forcing the whole vault.

policies/
  Rules for who can read, write, execute, publish, merge, settle, or escalate.

receipts/
  Audit logs proving source, transformation, validation, and final state.
```

## Immutable Source Rule

Everything saved into `sources/` is immutable.

Do not rewrite source history.

If a source is wrong, stale, incomplete, or contradicted, add a correcting source and compile the correction into the knowledge layer.

## Separate the Layers

Do not blur source, ontology, compiled knowledge, policy, and receipt layers.

```text
source evidence is not interpretation
ontology is not prose
knowledge is not raw evidence
policy is not a suggestion
receipt is not decoration
```

Trust comes from clean boundaries.

## Compile, Do Not Merely Retrieve

Retrieval gives the agent chunks.

Compilation gives the agent a maintained structure.

AGENTROPOLIS should answer from compiled knowledge whenever possible, then cite or trace back to immutable sources when verification is needed.

## Link Everything

Every important entity should connect to other entities through explicit edges.

Examples:

- agent to district
- district to tool
- tool to MCP lane
- workflow to policy
- policy to authority level
- source to claim
- claim to receipt
- receipt to execution

The value is in the edges, not only the pages.

## Navigate by Index

Agents should not load the entire vault for every answer.

They should start with indexes, follow relevant entity links, synthesize, then stop.

If the agent must brute-force the whole vault, the index needs repair.

## Lint the Knowledge

Run health checks against the ontology and compiled knowledge.

Lint checks should detect:

- orphan entities
- duplicate entities
- spelling drift
- canon conflicts
- stale claims
- uncited claims
- missing links
- policy violations
- receipt gaps
- contradictory pages

A contradiction is not failure. A contradiction is signal.

## Start Small

Begin with a small, high-value ontology slice before scaling.

Recommended first slices:

- AGENTROPOLIS core doctrine
- district registry
- MCP capability registry
- loop registry
- policy and authority model
- receipt schema

## Doctrine Lock

```text
Sources are immutable.
Ontology creates structure.
Knowledge is compiled.
Indexes make retrieval focused.
Loops maintain the graph.
Policies govern action.
Receipts prove the work.
```

This is the knowledge foundation for Agentropolis.
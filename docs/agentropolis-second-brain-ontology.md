# AGENTROPOLIS Second Brain Ontology Doctrine

Status: active infrastructure doctrine

## Core lock

AGENTROPOLIS does not use AKIRA CODEX for infrastructure memory.

AKIRA CODEX remains WIRED CHAOS lore only.

AGENTROPOLIS uses:

- AGENTROPOLIS ONTOLOGY
- AGENTROPOLIS KNOWLEDGE GRAPH
- Agent memory
- Repo memory
- Build logs
- Execution logs
- Operator-approved automation

## Purpose

This doctrine adapts the second-brain workflow pattern into AGENTROPOLIS as a persistent agent operating system.

The goal is not just to remember conversations. The goal is to convert conversations, repositories, builds, prompts, workflows, and outcomes into a living ontology that agents can read from and write back to.

## Architecture

```text
Ingest
  -> Extract
  -> Normalize
  -> Connect
  -> Approve
  -> Execute
  -> Log
  -> Learn
```

## Inputs

AGENTROPOLIS may ingest:

- ChatGPT conversations
- Hermes sessions
- Codex sessions
- GitHub repos, commits, issues, and pull requests
- Operator notes
- Voice memos
- Documents
- Financial and business data
- Creator assets
- Automation logs

## Entity model

Every memory object should resolve into one or more ontology entities:

- Person
- Project
- Repository
- Agent
- Skill
- Workflow
- Prompt
- Document
- Decision
- Task
- Output
- Metric
- Risk
- Rule
- Canon lock

## Write-back rule

Agents do not only answer. They must write useful results back into the ontology when the result creates reusable knowledge.

Examples:

- A new project decision becomes a Decision entity.
- A repeated instruction becomes a Rule entity.
- A build pattern becomes a Workflow entity.
- A useful prompt becomes a Prompt entity.
- A repository change becomes a Repo Memory entity.

## Approval rule

Before any autonomous workflow updates execution behavior, the operator must approve the discovered connections.

Recommended gate:

```text
Show discovered connections -> operator approves -> agents wire them into the ontology -> one test run -> review -> scheduled automation
```

## Agent lanes

Recommended AGENTROPOLIS lanes:

- Memory Agent
- Research Agent
- Builder Agent
- Creator Agent
- Distribution Agent
- Finance Agent
- Legal Agent
- Real Estate Agent
- Crypto Agent
- Security Agent
- Voice Agent
- Ontology Agent

## Repository role

This repository is the source of truth for the AGENTROPOLIS living ontology and knowledge graph schema.

It should define the entities, relations, memory rules, canon locks, approval gates, and write-back contracts used by the rest of the AGENTROPOLIS stack.

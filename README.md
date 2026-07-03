# AGENTROPOLIS-ONTOLOGY

AGENTROPOLIS-ONTOLOGY is a vendor-neutral, Apache-2.0 licensed public repository for describing an Agentropolis operating model. It provides baseline schemas, documentation, and examples for governed AI ecosystems built from districts, agents, skills, memory, policies, workflows, permissions, events, registries, and audits.

## Scope

This repository defines portable metadata and governance structures. It does **not** define a specific runtime, deployment platform, identity provider, or proprietary agent framework.

## Repository structure

- `/schemas` — JSON Schema definitions for core ontology objects
- `/districts` — district instance documents
- `/agents` — agent instance documents
- `/skills` — skill instance documents
- `/memory` — memory model instance documents
- `/policies` — policy instance documents
- `/workflows` — workflow instance documents
- `/permissions` — permission model instance documents
- `/events` — event instance documents
- `/registries` — registry instance documents
- `/audits` — audit artifact instance documents
- `/examples` — sample documents showing intended usage
- `/docs` — project overview and ontology design principles

## Included assets

- Apache License 2.0 licensing materials
- contribution, conduct, and security guidance
- baseline JSON schemas for districts, agents, skills, memory, policies, workflows, and events
- sample district and agent documents

## Security posture

- Schemas favor explicit structure and bounded enumerations where practical
- Sensitive material should be referenced, classified, or redacted rather than embedded directly
- Authorization, secrets handling, and audit requirements should be enforced by implementations in addition to these documents

## Trademark and lore notice

This repository's code and documents are licensed under Apache-2.0 unless stated otherwise. However, **Agentropolis names, lore, visual identity, logos, and trademarks are not licensed for reuse** by the Apache-2.0 license. Do not imply endorsement, affiliation, or brand reuse rights from this repository.

See `/docs/overview.md` and `/docs/ontology-principles.md` for more detail.

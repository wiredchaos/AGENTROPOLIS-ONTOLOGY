# Security Policy

## Scope

This repository contains documentation, schemas, and example artifacts for an ontology. It does not itself provide runtime isolation, identity, authorization, or secret management.

## Reporting a vulnerability

Please report suspected vulnerabilities privately to the maintainers instead of opening a public issue. Include:

- a clear description of the issue
- affected files or schemas
- reproduction steps or example payloads
- impact and recommended mitigation, if known

## Secure contribution guidance

- never commit secrets, tokens, credentials, or personal data
- treat example identifiers as non-production placeholders
- prefer references to sensitive resources instead of embedding secret values
- preserve auditability and least-privilege semantics when extending schemas

## Implementation warning

Consumers of this ontology must still enforce:

- authentication and authorization
- input validation
- secret storage and rotation
- data retention and deletion controls
- tamper-evident logging and audit review

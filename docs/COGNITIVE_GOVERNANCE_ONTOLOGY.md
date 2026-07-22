# Cognitive Governance Ontology

## Scope

This vocabulary models reasoning coverage on transactions and assessments. It does not assert machine consciousness, enlightenment, emotion, or a permanent psychological type for an agent.

## Classes

- `CognitiveFunction`
- `CognitiveAssessment`
- `CognitiveRequirement`
- `CognitiveConflict`
- `CognitiveCoverage`
- `CognitiveImbalance`
- `EvidenceArtifact`
- `OperationalDecision`

## CognitiveFunction instances

- `NI_FORESIGHT`
- `NE_SCENARIOS`
- `TI_CONSISTENCY`
- `TE_EXECUTION`
- `FI_INTEGRITY`
- `FE_IMPACT`
- `SI_PRECEDENT`
- `SE_REALITY`

## Relationships

| Relationship | Domain | Range | Meaning |
|---|---|---|---|
| `requiresFunction` | `Transaction` | `CognitiveFunction` | A transaction requires this reasoning lens before readiness. |
| `appliesFunction` | `CognitiveAssessment` | `CognitiveFunction` | The assessment uses this reasoning lens. |
| `evaluates` | `CognitiveAssessment` | `Plan`, `Mandate`, `Action`, or `EvidenceArtifact` | The subject being evaluated. |
| `supportedBy` | `CognitiveAssessment` | `EvidenceArtifact` | Evidence supporting the claim. |
| `counterbalancedBy` | `CognitiveFunction` | `CognitiveFunction` | Error-correction relationship. |
| `betweenFunction` | `CognitiveConflict` | `CognitiveFunction` | Functions participating in a conflict. |
| `resolvedBy` | `CognitiveConflict` | `OperationalDecision`, `PolicyDecision`, or `HumanReview` | Resolution authority or decision. |
| `derivedFrom` | `OperationalDecision` | `CognitiveAssessment` | Assessment informing a decision. |
| `constrainedBy` | `OperationalDecision` | `Mandate`, `Policy`, or `Authority` | Governing constraint. |

## Counterweight pairs

```text
NI_FORESIGHT   <-> SE_REALITY
NE_SCENARIOS   <-> SI_PRECEDENT
TI_CONSISTENCY <-> FE_IMPACT
TE_EXECUTION   <-> FI_INTEGRITY
```

## Modeling rule

Correct:

```text
Transaction deploy_8421 requiresFunction SE_REALITY
Assessment assessment_91 appliesFunction SE_REALITY
Assessment assessment_91 supportedBy health_check_8472
```

Incorrect:

```text
Agent router_01 hasPersonality NI
```

The ontology classifies the reasoning used in a specific context. It must not stereotype an agent as permanently belonging to a human personality category.

## Minimal JSON representation

```json
{
  "type": "CognitiveAssessment",
  "id": "assessment_91",
  "appliesFunction": "SE_REALITY",
  "evaluates": "action:deploy_8421",
  "claim": "The staging target is healthy.",
  "supportedBy": ["evidence:health_check_8472"],
  "confidence": 0.94,
  "requiresHumanReview": false
}
```

## Governance invariant

A cognitive assessment can inform, challenge, or block an operational decision. It cannot grant itself authority, alter the mandate, or self-certify missing evidence.

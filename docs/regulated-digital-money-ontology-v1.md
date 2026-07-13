# Regulated Digital Money Ontology v1

## Status

Draft canonical contract for Agentropolis.

This document defines the source-of-truth vocabulary and relationships for regulated digital money across ONTOLOGY OS, PAYRAIL, NEURA, AGENT SEATBELTS, FIN54, and HUB.

It does not authorize custody, token issuance, bank representation, or live autonomous settlement.

## Layer placement

```text
Infrastructure
  ONTOLOGY OS -> canonical meaning and policy contracts
  AGENT SEATBELTS -> authority and approval enforcement
  PAYRAIL -> payment execution and receipts

Districts and institutions
  NEURA -> treasury, accounting, tax, and reconciliation
  FIN54 -> financial and regulatory intelligence

Applications
  HUB and city surfaces -> status, controls, and operator visibility
```

## Core entities

### AssetClass

Canonical values:

- `fiat_bank_deposit`
- `tokenized_bank_deposit`
- `regulated_stablecoin`
- `cryptoasset`
- `closed_loop_credit`
- `tokenized_security`
- `tokenized_rwa`

### PaymentIntent

A normalized request to move value. A PaymentIntent is not itself authorization or settlement.

Required relationships:

```text
PaymentIntent
  requestedBy -> Agent | Human | Application
  referencesAsset -> AssetClass
  pays -> Recipient
  constrainedBy -> Jurisdiction
  constrainedBy -> CompliancePolicy
  constrainedBy -> SpendingAuthority
  evaluatedBy -> PolicyDecision
  approvedBy -> HumanApproval? 
  routedThrough -> SettlementRail?
  providedBy -> Provider?
  produces -> Receipt
  produces -> AccountingEvent
  produces -> AuditEvent
```

### SettlementRail

Canonical values may include:

- `ach`
- `wire`
- `card`
- `base_usdc`
- `xrpl_xrp`
- `xrpl_rlusd`
- `tokenized_deposit_network`

A rail definition must not imply that a provider relationship or production entitlement exists.

### Provider

A regulated or technical service capable of exposing one or more SettlementRail capabilities.

Required fields:

- provider identity
- legal entity
- jurisdiction
- capability status
- supported asset classes
- supported rails
- custody role
- compliance requirements
- production access state

### SpendingAuthority

Defines the maximum authority delegated to an agent or application.

Required fields:

- principal
- agent or application identity
- allowed asset classes
- allowed rails
- per-transaction limit
- rolling-period limit
- recipient constraints
- purpose constraints
- human approval threshold
- expiration
- revocation state

### PolicyDecision

Canonical outcomes:

- `allow_simulation`
- `require_human_approval`
- `allow_restricted_live`
- `deny`

Each decision must include a reason code and the ontology version used.

### RegulatedDigitalMoneyCapability

Canonical states:

- `disabled`
- `sandbox`
- `restricted_live`
- `production`

No implementation may infer `production` from legislation, a pilot announcement, or technical availability alone.

## Required semantic distinctions

1. A tokenized bank deposit is a liability of the issuing bank.
2. A regulated stablecoin is an issuer-backed payment token with its own legal and reserve structure.
3. A cryptoasset is not a bank deposit.
4. A closed-loop credit is not customer money, a bank deposit, or an insured balance.
5. A tokenized security or RWA is a restricted asset class and must not be treated as ordinary payment money.
6. A provider pilot is not equivalent to public production access.
7. A law taking effect is not equivalent to licensing, provider onboarding, or operational approval.

## Validation rules

An Agentropolis component must reject or flag any record that:

- labels a cryptoasset or internal credit as a deposit
- claims deposit insurance without an identified regulated issuer and verified coverage basis
- omits issuer or provider identity for a regulated asset
- omits jurisdiction for live or restricted-live execution
- permits an agent to exceed its SpendingAuthority
- lacks a human approval reference above the configured threshold
- lacks an idempotency key for an irreversible payment
- lacks a policy decision and audit event

## Activation gates

Production capability requires all gates to be true:

- lawful provider production access
- legal role review complete
- money-transmission analysis complete
- custody role defined
- KYC, AML, sanctions, and transaction-monitoring controls operational
- disclosures approved
- reconciliation and tax reporting tested
- key management and incident response tested
- emergency freeze and provider revocation available
- human approval and spending limits enforced

## Event model

Every attempted payment must generate:

1. `payment_intent_created`
2. `policy_decision_recorded`
3. `human_approval_recorded` when required
4. `rail_selected` or `rail_selection_failed`
5. `simulation_completed` before live execution
6. `settlement_submitted` only when authorized
7. `settlement_confirmed` or `settlement_failed`
8. `accounting_event_recorded`
9. `audit_event_sealed`

## Cross-repo ownership

| Repository | Ownership |
|---|---|
| AGENTROPOLIS-ONTOLOGY | Canonical vocabulary, relationships, validation rules, versioned contracts |
| AGENTROPOLIS-PAYRAIL | Execution, adapters, routing, simulation, approvals, receipts, replay protection |
| NEURA / NuraTax | Treasury, accounting, tax classification, reconciliation, reporting |
| AGENT SEATBELTS NMX | Delegated authority, limits, revocation, irreversible-action controls |
| FIN54 | Regulatory and institutional monitoring signals |
| AGENTROPOLIS-HUB | Registry, status, and cross-repo coordination |

## Versioning

Consumers must record the ontology version on every PaymentIntent, PolicyDecision, Receipt, AccountingEvent, and AuditEvent.

Initial version identifier:

```text
agentropolis.regulated-digital-money.v1
```

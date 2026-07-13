# Regulated Digital Money Cross-Repository Map

## Canonical source

All repositories in this map consume `agentropolis.regulated-digital-money.v1` from AGENTROPOLIS-ONTOLOGY.

No consumer repository may redefine asset classes, capability states, payment intent semantics, or regulatory activation gates locally.

## Repository responsibilities

| Repository | Role | Required integration | Prohibited behavior |
|---|---|---|---|
| `HERMES-CITY` | Public coordination and signal layer | Explain status, route approved requests to MCP, show public-safe receipts | No custody, no direct settlement, no claims of bank access |
| `AGENTROPOLIS-CREATOR` | Construction District and Foundry | Generate approved UI, schema docs, dashboards, simulations, and integration packages | No finance logic, no payment execution, no local asset ontology |
| `AGENTROPOLIS-DEPLOY` | Deployment control plane | Package versioned schemas, feature flags, bindings, secrets isolation, rollback, observability | No ecosystem-wide secrets, no automatic production activation |
| `AGENTROPOLIS-GAMING-DISTRICT` | Gaming shared services | Keep real-money and real-value flags false by default; consume PAYRAIL only through separately approved payout lanes | No conversion of credits, bounties, prediction rounds, or gameplay claims into regulated money without separate review |
| `AGENTROPOLIS-GTM` | Distribution and revenue workflow layer | Create payment intents for approved commercial actions and route them through MCP/PAYRAIL | No fabricated settlement, no bypass of approvals, no autonomous outreach-linked payments |
| `AGENTROPOLIS-AGENT-MCP` | Governed tool and execution membrane | Validate authority, ontology version, provider capability, human approval, and receipts before invoking PAYRAIL | No raw wallet keys, no unrestricted bank or settlement tools |
| `ASBE` | Agentic Studio Build Engine orchestration layer | Treat billing and creator payouts as external governed intents routed through MCP/PAYRAIL | No embedded settlement engine, no duplicate financial contracts |
| `AGENTROPOLIS-FIN54` | Financial and regulatory intelligence | Monitor laws, bank pilots, provider availability, filings, and risk signals; publish evidence with timestamps | No payment execution, no legal-availability inference from headlines alone |
| `AGENTROPOLIS-54T` | Domain application consumer | Use canonical intent, authority, receipt, and accounting references when financial workflows are introduced | No local token/deposit semantics |
| `AGENTROPOLIS-HRM54` | Human resources domain consumer | Route payroll-adjacent or reimbursement intents through approved finance services and human approvals | No autonomous payroll movement or employee-fund custody |
| `54-FISCAL-CMD` | Fiscal command and finance-critical operations | Consume ontology contracts; perform accounting, compliance state, fiscal controls, and settlement-adjacent logic in Rust-first services | No production finance in prototype TypeScript; no direct live rail activation before review |

## Execution chain

```text
Human or agent intent
  -> HERMES-CITY or domain application
  -> AGENTROPOLIS-AGENT-MCP
  -> ontology validation
  -> authority and human approval check
  -> AGENTROPOLIS-PAYRAIL simulation
  -> provider capability and activation gates
  -> settlement only when authorized
  -> receipt
  -> NEURA / 54-FISCAL-CMD accounting and reconciliation
  -> FIN54 monitoring and external signal updates
  -> HUB status
```

## Deployment flags

Production deployments must define these as disabled unless a reviewed environment explicitly overrides them:

```text
PAYRAIL_REGULATED_DIGITAL_MONEY=disabled
PAYRAIL_TOKENIZED_DEPOSITS=disabled
NEURA_REGULATED_DIGITAL_MONEY=disabled
GAMING_REAL_MONEY_ENABLED=false
GAMING_REAL_VALUE_ENABLED=false
```

## Consumer contract

Every consumer must carry:

- `ontologyVersion`
- `paymentIntentId`
- `policyDecisionId`
- `humanApprovalId` when required
- `receiptId`
- `accountingEventId` when applicable
- `auditEventId`

## Boundary rule

A user interface, workflow, game event, GTM conversion, studio job, HR action, or fiscal plan may create a PaymentIntent. It may not silently become authorization or settlement.

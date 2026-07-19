# ONTOLOGY Identity Entity Evidence Audit

**Repository:** `wiredchaos/AGENTROPOLIS-ONTOLOGY`  
**Commit reviewed:** `4b518f5a2b5bdc83559e198ec32c317ef989c088`  
**Audit date (UTC):** `2026-07-19`  
**Audit mode:** read-only evidence audit (no production behavior changes; no registry mutation)  
**Auditor:** Cursor cloud agent  
**Cloud agent:** https://cursor.com/agents/bc-e330c126-dfc8-429e-b045-c9010d6f31dd  
**Controlling authority referenced:** `wiredchaos/agentropolis` canon, federation hardening, repository registry, Issue #85 (not fetchable from this environment; `wiredchaos/agentropolis` returns 404 here). Audit grounded in ONTOLOGY tree evidence, including unmerged remote branches.

**Prior confirmed non-candidates (identity authority):**

| Repository | Actual function | Identity status |
|---|---|---|
| `AGENTROPOLIS-SOVEREIGNTY` | Provider/model sovereignty router | EMPTY-SHELL for identity |
| `AGENTROPOLIS-ATG` | Trust doctrine, schemas and prototype | EMPTY-SHELL for identity |

---

## 1. Executive summary

**AGENTROPOLIS-ONTOLOGY is not the AGENTROPOLIS identity authority, and it does not currently contain a complete or normative identity-entity model that a dedicated Identity Authority could safely treat as already owned.**

On `main` (`4b518f5`), the repository is a **documentation + schema-stub package** for:

1. compiled-knowledge / second-brain ontology doctrine;
2. Obsidian + gbrain claim attribution shapes;
3. regulated digital money vocabulary and one JSON Schema envelope;
4. a source-evidence JSON Schema.

There is **no** runtime, package manifest, API, database, auth, credential service, principal registry, agent identity binding, mandate/delegation engine, session store, wallet linker, revocation bus, receipt/audit emitter, test suite, or CI workflow.

Identity-adjacent vocabulary appears only as:

- **knowledge-graph entity labels** (Person, Agent, relationship, claim holders) in doctrine docs;
- a **prose field name** `principal` inside `SpendingAuthority` (regulated digital money), without a Principal schema;
- an **unmerged** scaffold branch (`origin/copilot/agentropolis-ontology-structure` @ `2b23c055`) with a descriptive `Agent` JSON Schema that is explicitly **not** an identity provider / authority runtime.

**Final recommendation for identity-authority status:** `EMPTY-SHELL`  
**Actual implemented roles:** documentation-only package · schema-only package (knowledge + regulated-money stubs) · aspirational entity vocabulary (docs / unmerged scaffold)

**Control-question answer:** Identity entities do **not** already exist here in a form that should block creating a dedicated Identity Authority. Partial **descriptive** seeds exist and must be coordinated to avoid semantic drift — they are not a substitute for root identity contracts or enforcement.

---

## 2. Actual repository role

### Classification (tree evidence)

| Candidate role | Verdict | Evidence |
|---|---|---|
| canonical identity authority | **No** | No principal/agent binding, credentials, sessions, mandates, revocation, or persistence |
| identity entity schema home (normative) | **No (on main)** | No `principal` / `credential` / `mandate` / `delegation` / `session` / `wallet-as-identity` schemas on `main` |
| knowledge / domain ontology | **Yes (docs + stubs)** | Second-brain doctrine, claim ontology, regulated-money vocab |
| descriptive agent/district metadata schema | **Partial (unmerged only)** | `schemas/agent.schema.json` on structure branch; not on `main` |
| authorization / credential runtime | **No** | Structure-branch README: does not define IdP or runtime |
| wallet / payment identity layer | **No** | Money schema uses free-string `requestedBy`; no wallet identity model |
| duplicate of ATG identity protocol | **No** | Different surface (knowledge + money), no Trusted Authorization Path |
| empty shell (identity authority) | **Yes** | Identity-authority domain has no enforceable controls |

### Evidence surfaces inspected (`main`)

| Surface | Present? | Path / note |
|---|---|---|
| Tracked files | 12 | LICENSE, README, 8 docs, 2 schemas |
| Package metadata | **Absent** | No `package.json`, `pyproject.toml`, `Cargo.toml`, `go.mod` |
| Runtime / `src/` | **Absent** | None |
| APIs / MCP / servers | **Absent** | None |
| Schemas | 2 JSON Schemas | `schemas/source.schema.json`, `schemas/regulated-digital-money-v1.schema.json` |
| Tests / CI | **Absent** | No `tests/`, no `.github/workflows` |
| Registries / governance | **Absent on main** | Created only by this audit PR as proposed artifacts |
| Database / migrations | **Absent** | None |

### Unmerged branches inspected (not evidence of `main` ownership)

| Branch | Tip | Relevance |
|---|---|---|
| `origin/copilot/agentropolis-ontology-structure` | `2b23c055c3601de3fef3537a207d225bd89809e8` | Scaffold schemas: agent, district, policy, skill, memory, workflow, event + samples |
| `origin/ontology-economic-layer` | `3c7567f295943e67cc70ad9f271578eec05a1d8e` | Capital / value / convergence-risk schemas; `owner_ref` string only |
| `origin/codex/regulated-digital-money-ontology` | merged into `main` via PR #2 | Same regulated-money content as `main` |

### README / doctrine claims vs confirmation

| Claim | Status |
|---|---|
| Open ontology for districts, agents, skills, memory, policies, workflows, permissions, events, registries, audits | **Claim / aspiration on `main`** — directories and most schemas absent; only money + source schemas exist |
| Source of truth for living ontology and knowledge graph schema | **Doctrine claim** (`docs/agentropolis-second-brain-ontology.md`) — entity list is prose, not schemas |
| Backend/MCP own auth and identity | **Confirmed boundary** (`docs/agent-runtime-position.md`) — places identity outside this repo |
| Identity and wallets map to sovereign identity and payment rails | **Research intake only** (`docs/research/awesome-agent-cortex.md`) — not a schema |
| Structure-branch: does not define IdP / runtime | **Confirmed** (branch README Non-goals / Scope) |

---

## 3. Architecture map

```text
┌──────────────────────────────────────────────────────────────┐
│ AGENTROPOLIS-ONTOLOGY @ 4b518f5 (main)                       │
│                                                              │
│  docs/                                                       │
│    second-brain / compiled-knowledge doctrine                │
│    Obsidian + gbrain claim shapes                            │
│    regulated digital money vocabulary                        │
│    runtime-position: identity owned by backend/MCP           │
│                                                              │
│  schemas/                                                    │
│    source.schema.json                                        │
│    regulated-digital-money-v1.schema.json                    │
│      paymentIntent.requestedBy: string                       │
│      (no Principal / Agent / Credential objects)             │
└──────────────────────────────────────────────────────────────┘
        │ does NOT enforce
        ▼
   (no runtime / no identity PDP)

Unmerged scaffold (NOT on main):
┌──────────────────────────────────────────────────────────────┐
│ origin/copilot/agentropolis-ontology-structure @ 2b23c055    │
│  schemas/agent.schema.json  — descriptive actor metadata     │
│  owners[] string labels; permissions scopes; no principal_id │
│  README: not an identity provider                            │
└──────────────────────────────────────────────────────────────┘
```

---

## 4. Entity inventory (identity control question)

### 4.1 Required identity-authority entities vs evidence

| Entity | On `main`? | Elsewhere? | Notes |
|---|---|---|---|
| human principal | **No schema / runtime** | Prose field name `principal` under SpendingAuthority | Not a typed Principal; no lifecycle |
| organization | **No** | Claim holder path `companies/<slug>` (docs) | Attribution slug, not org registry |
| agent (identity binding) | **No on main** | Structure-branch `agent.schema.json`; doc entity “Agent” | Descriptive ontology actor, not authenticated agent identity |
| service account | **No** | — | |
| wallet (linked identifier lifecycle) | **No** | Cross-repo map forbids raw wallet keys in MCP | No wallet identity schema |
| device | **No** | — | |
| session | **No** | — | |
| credential | **No** | Structure-branch SECURITY.md says never commit credentials | Policy text only |
| mandate | **No** | — | |
| delegation | **No** | Seatbelts named as external owner for delegated authority | |
| capability (identity/authz) | **Partial / different** | Money `capability.status` enum; skill “callable capability” on structure branch | Not principal capability grants |
| revocation | **No** | Prose “revocation state” on SpendingAuthority; provider freeze gate | No revocation schema/bus |
| receipt / audit (identity) | **No** | Money event model + source `receipt_id` string | Not `agentropolis.receipt.v1` / identity audit |
| relationship (graph) | **Docs only** | Claim kind `relationship`; doctrine “Link Everything” | Knowledge edges, not authority edges |
| authority (root) | **No** | SpendingAuthority prose; “policy to authority level” prose | Domain authority language ≠ Identity Authority |

### 4.2 Entities that *do* exist (ontology / money domain — not identity authority)

| Entity / concept | Path | Form | Identity relevance |
|---|---|---|---|
| Source | `schemas/source.schema.json` | JSON Schema | Provenance for knowledge; not authN |
| PaymentIntent envelope | `schemas/regulated-digital-money-v1.schema.json` | JSON Schema | `requestedBy` free string |
| AssetClass / PolicyDecision / Capability status | `docs/regulated-digital-money-ontology-v1.md` + schema | vocab + enum | Finance domain |
| SpendingAuthority | docs only | Required fields list includes `principal` | **Drift risk** if left unbound to Identity Authority types |
| Person / Agent / Project / … | `docs/agentropolis-second-brain-ontology.md` | Prose entity list | Knowledge entities |
| Claim holder / subject | `docs/obsidian-gbrain-intelligence-layer.md` | Example JSON shape | Attribution, not credentials |
| Agent (scaffold) | structure-branch `schemas/agent.schema.json` | JSON Schema | Optional `owners[]` strings; `permissions.scopes`; no principal binding |
| District / Policy / Skill / Memory / Workflow / Event | structure-branch schemas | JSON Schema | Governance metadata vocabulary |
| Capital / Value | economic-layer branch | JSON Schema | `owner_ref` opaque string |

### 4.3 Distinction check

| Required distinction | Status |
|---|---|
| human ≠ agent ≠ wallet ≠ session ≠ role ≠ capability ≠ mandate ≠ delegation ≠ credential | **Not implemented** — no typed identity suite |
| Wallet not treated as complete identity | **N/A on main** (no wallet model); research doc conflates “Identity and wallets” only as cortex mapping |
| Agent cannot be self-rooted | **Not enforceable** — no agent registry; scaffold `owners[]` is optional free strings |
| Knowledge Agent ≠ Identity Agent | **At risk of drift** — same word “Agent” used for ontology actor and (elsewhere) identity subject |

---

## 5. Authorization control flow

Target federation path:

`request → authentication → principal resolution → agent resolution → mandate lookup → capability evaluation → policy decision → execution permission → receipt → audit / revocation`

### Stage-by-stage evidence (`main`)

| Stage | Status | Evidence |
|---|---|---|
| request | **missing** | No API |
| authentication | **missing** | None |
| principal resolution | **missing** | SpendingAuthority prose only |
| agent resolution | **missing** | Doc/scaffold labels only |
| mandate lookup | **missing** | None |
| capability evaluation | **missing for identity** | Money capability status fields only |
| policy decision | **schema stub (money)** | `policyDecision.outcome` enum in money schema — not a PDP |
| execution permission | **missing** | Explicitly deferred to PAYRAIL / Seatbelts / MCP in cross-repo map |
| receipt | **missing (identity)** | Money event list + source `receipt_id` |
| audit / revocation | **missing** | No emitters |

**Closest implemented path:** none for identity. Closest domain path is documentation of payment intent → policy → human approval → PAYRAIL, owned by other repos.

---

## 6. Human authority

| Control | Status | Evidence |
|---|---|---|
| Every agent has accountable human/org principal | **missing** | Structure-branch `owners[]` optional; no principal type |
| Agents cannot self-register into authority | **missing** | No registration surface |
| Human approval gates | **documented (money / workflows)** | `requiresHumanApproval`, workflow step kind `approval` (unmerged) — not identity issuance |
| Emergency halt / Mission Control | **missing here** | Named externally in sibling audits / money activation gates |

---

## 7. Schema / contract honesty

### Present on `main`

1. `schemas/source.schema.json` — knowledge source immutability metadata.  
2. `schemas/regulated-digital-money-v1.schema.json` — payment intent + capability + optional policyDecision.  
   - `requestedBy` is an unconstrained string (not `principal_id` / `agent_id`).  
   - No SpendingAuthority object despite docs requiring it.

### Present only on unmerged structure branch

- `agent.schema.json`, `district.schema.json`, `policy.schema.json`, `skill.schema.json`, `memory.schema.json`, `workflow.schema.json`, `event.schema.json`
- Explicit non-goal: identity provider

### Absent everywhere inspected

- `principal.schema.json` / `agentropolis.principal.v1`
- credential / session / device / wallet-link schemas
- mandate / delegation / revocation / identity receipt schemas
- DID / VC / JWT / OIDC / Passkey bindings
- Conformance fixtures for identity fail-closed behavior

---

## 8. Semantic drift risk (why this audit matters before creating Identity Authority)

Creating a dedicated Identity Authority **without** coordinating vocabulary would risk duplicate models, but the inverse error is worse: treating this repo as already owning identity because the words “Agent”, “principal”, and “relationship” appear in docs.

| Drift vector | Location | Mitigation |
|---|---|---|
| “Agent” as knowledge actor vs authenticated subject | second-brain docs; structure-branch agent schema | Identity Authority owns authenticated agent records; ONTOLOGY may reference `agent_id` |
| SpendingAuthority.`principal` unbound | `docs/regulated-digital-money-ontology-v1.md` | Bind to Identity Authority principal id once designated; do not invent a second Principal type here |
| Claim holders `people/<slug>` / `agents/<slug>` | gbrain claim shape | Keep as knowledge attribution paths; do not equate to auth principals |
| Research map “Identity and wallets” | awesome-agent-cortex.md | Treat as research radar, not canon |
| Structure-branch merge without identity review | unmerged PR-less branch | If merged later, require explicit “descriptive metadata only” banner + foreign-key refs to Identity Authority |

**Conclusion for sequencing:** Safe to designate/create Identity Authority after PAY-PROTOCOL audit; ONTOLOGY should remain vocabulary/knowledge/money-contract home and **consume** identity identifiers rather than mint root authority.

---

## 9. Cross-repo ownership (evidence-based recommendation)

| Concern | Recommended owner | ONTOLOGY role |
|---|---|---|
| Normative trust/authZ message schemas (`principal`, `mandate`, `delegation`, `receipt`, `revocation`) | **ATG** (protocol track; currently EMPTY-SHELL stubs elsewhere) | May mirror/import for documentation; must not fork conflicting semantics |
| Principal/agent registry, credentials, sessions, enforcement, halt | **Dedicated Identity Authority** (to designate/create) | Consumer of IDs in entity links |
| District/agent/skill/memory/policy/workflow **descriptive** ontology | **ONTOLOGY** | Own knowledge/governance metadata schemas |
| Regulated digital money vocabulary | **ONTOLOGY** | Already drafting `agentropolis.regulated-digital-money.v1` |
| Payment execution / wallet custody | **PAY-PROTOCOL / PAYRAIL** (next audit) | Separate payment identity from root identity |
| Model/provider sovereignty routing | **SOVEREIGNTY** | Unrelated to identity entities |

---

## 10. Scores (as identity-authority candidate, 0–5)

| Dimension | Score | Rationale |
|---|---|---|
| human accountability | 0 | No principals |
| identity clarity | 1 | Vocabulary seeds only; ambiguous Agent/principal wording |
| wallet separation | 0 | No wallet identity model |
| revocation | 0 | None |
| authorization boundaries | 1 | Docs defer enforcement elsewhere |
| portability | 3 | Vendor-neutral docs; no IdP lock-in because no IdP |
| auditability | 1 | Receipt language without identity audit schema |
| recovery | 0 | None |
| privacy | 2 | Sensitivity labels in doctrine/scaffold; no privacy program |
| test coverage | 0 | No tests |
| operational readiness | 0 | Docs/schemas only |

**Aggregate:** ~0.7 / 5 for identity-authority suitability.

---

## 11. Severity-ranked findings

### P0

1. **No identity authority controls** — cannot bind agents to humans via this repo.  
2. **Registry misclassification risk** — README “agents / permissions / audits” language can be over-read as identity ownership.  
3. **Unbound `principal` in SpendingAuthority prose** — consumers may invent local principal types.

### P1

4. **Semantic drift** between knowledge `Agent`, scaffold `agent.schema.json`, and future Identity Authority `agent`.  
5. **Money schema under-implements documented SpendingAuthority** — gaps invite ad-hoc identity fields in PAY consumers.  
6. **`wiredchaos/agentropolis` / Issue #85 / live registry not fetchable** — proposed patch only; do not auto-apply; do not treat ATG PR #8 alone as final registry decision.

### P2

7. Structure-branch schemas useful for ontology metadata but not merged; merging without identity boundary notes increases confusion.  
8. No conformance tests for any identity-adjacent claims.

### P3

9. Align README with what `main` actually ships (knowledge + regulated-money stubs).  
10. Record EMPTY-SHELL identity status in federation registry once assembled in `wiredchaos/agentropolis`.

---

## 12. Final status recommendation

### For identity federation role

**EMPTY-SHELL**

Do **not** mark CANONICAL, ACTIVE, ADAPTER, or LEGACY identity. Do **not** treat descriptive Agent/Person/relationship vocabulary as an existing Identity Authority entity suite.

Confidence: **high (0.93)**

### For this repository’s true domain (informational)

Register as **ACTIVE / INCUBATING ontology & knowledge-contract package** for:

- compiled knowledge doctrine;
- regulated digital money vocabulary;
- (future) descriptive district/agent/skill/… metadata schemas.

Canon promotion for ontology should wait for merged normative schemas, validation tooling, and explicit foreign-key contracts to Identity Authority / ATG types.

---

## 13. Immediate next actions

1. Publish this evidence pack; keep registry patch **proposed only**.  
2. Audit `wiredchaos/AGENTROPOLIS-PAY-PROTOCOL` next (separate wallet/payment identity from root identity).  
3. Assemble a **cross-repository** registry patch in `wiredchaos/agentropolis` covering SOVEREIGNTY + ATG + ONTOLOGY (+ PAY after audit). **Do not merge ATG PR #8 as a final registry decision until that assembly lands.**  
4. Designate or create Identity Authority runtime to enforce ATG normative contracts; ONTOLOGY references those IDs in entity models.  
5. If structure-branch agent schemas are merged later, require `principal_ref` / external identity ids rather than inventing local root identity.

## 14. Codex / Cursor required next

**YES** — next evidence pass: `wiredchaos/AGENTROPOLIS-PAY-PROTOCOL`, then designate/create Identity Authority and assemble the hub registry patch.

---

## Answer to the control question

ONTOLOGY is **neither** the live identity authority **nor** a completed identity-entity schema home.

It is a **knowledge / domain ontology documentation + schema-stub surface** with **partial descriptive seeds** (Agent/Person/relationship prose; unmerged agent metadata schema; unbound SpendingAuthority `principal` field name). Those seeds must be coordinated to prevent semantic drift, but they **do not** already constitute principal, credential, authority, mandate, session, or wallet-identity models sufficient to skip a dedicated Identity Authority.

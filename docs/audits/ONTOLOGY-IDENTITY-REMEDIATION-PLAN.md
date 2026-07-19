# ONTOLOGY Identity Remediation Plan

**Repository:** `wiredchaos/AGENTROPOLIS-ONTOLOGY`  
**Commit reviewed:** `4b518f5a2b5bdc83559e198ec32c317ef989c088`  
**Companion evidence:** `docs/audits/ONTOLOGY-IDENTITY-EVIDENCE-AUDIT.md`  
**Machine record:** `governance/ontology-identity-evidence.yaml`  

**Scope rule:** Remediates **identity-boundary honesty and semantic-drift prevention**. Does **not** authorize turning this repo into an identity runtime, rotating secrets, deleting files, auto-applying the federation registry, or merging ATG PR #8 as a final registry decision.

---

## Decision premise

ONTOLOGY is **EMPTY-SHELL for identity authority**. Remediation has three tracks:

1. **Honesty track (this repo):** stop over-readable claims that this package already owns identity entities/runtime.  
2. **Vocabulary track (this repo):** keep knowledge / district / money ontology ownership; when entity schemas land, **reference** Identity Authority / ATG identifiers rather than forking root identity types.  
3. **Federation track (hub):** assemble a cross-repo registry patch in `wiredchaos/agentropolis` after sibling audits; do not treat single-repo proposed patches as final.

Do not grow ONTOLOGY into the Identity Authority.

---

## P0 — Authority defects and misclassification

### P0-1 — Correct registry classification (external apply, human-gated)

- **Problem:** ONTOLOGY can be misread as already owning principal/agent/credential models.  
- **Action:** Apply (manually, as part of the assembled hub patch) `docs/audits/ONTOLOGY-IDENTITY-REGISTRY-PATCH.proposed.yaml` into `wiredchaos/agentropolis/governance/repository-registry.yaml`.  
- **Target status:** `EMPTY-SHELL` for identity authority; optional `INCUBATING` / `ACTIVE` for ontology/knowledge contracts.  
- **Acceptance:** Registry does not list ONTOLOGY as CANONICAL identity; notes descriptive vocabulary vs root identity.

### P0-2 — Do not invent competing Principal / Credential schemas here

- **Problem:** SpendingAuthority prose requires `principal`; structure-branch Agent schema has optional `owners[]`.  
- **Action:**  
  - Forbid landing `principal.schema.json` / credential / session / mandate schemas in ONTOLOGY that compete with ATG normative identity contracts.  
  - When money or agent metadata schemas need accountability fields, use opaque foreign keys (`principal_id`, `agent_id`) whose normative types live in ATG + Identity Authority.  
- **Acceptance:** No second root Principal type ships from this repo.

### P0-3 — Preserve create-Identity-Authority path

- **Problem:** Partial vocabulary seeds could be used as an excuse to skip a dedicated runtime.  
- **Action:** Treat seeds as non-blocking. After PAY-PROTOCOL audit, designate or create Identity Authority that enforces ATG contracts.  
- **Acceptance:** Canon shows a non-ONTOLOGY owner for identity enforcement.

### P0-4 — Hub registry assembly gate

- **Problem:** Per-repo proposed patches (SOVEREIGNTY, ATG PR #8, this PR) are not a final registry decision.  
- **Action:** Assemble one cross-repository patch in `wiredchaos/agentropolis`. **Do not merge ATG PR #8 as final registry decision until that assembly lands.**  
- **Acceptance:** Hub registry lists SOVEREIGNTY + ATG + ONTOLOGY (+ PAY when audited) with evidence links.

---

## P1 — Binding vocabulary without becoming the authority

### P1-1 — Bind SpendingAuthority.principal

- Update regulated-money docs (and future schema objects) so `principal` / `agent or application identity` are explicitly **Identity Authority identifiers**, not locally defined person strings.  
- Prefer fields like `principal_id`, `agent_id`, `application_id` with `$ref` or documented URI patterns from ATG once published.

### P1-2 — Structure-branch Agent schema (if/when merged)

- Keep descriptive role: district actor metadata, skills, policy refs.  
- Add required or strongly recommended `principal_ref` / `identity_agent_id` pointing outward.  
- Retain README non-goal: not an identity provider.  
- Do not add credential issuance, session, or mandate fields to ontology Agent objects.

### P1-3 — Knowledge claim holders vs principals

- Document that `people/<slug>`, `agents/<slug>`, `companies/<slug>` are **attribution paths** for gbrain/Obsidian claims, not authentication principals.  
- Optional later: mapping table from claim holder → principal_id maintained by Identity Authority or a sync adapter — not by silent string equality.

### P1-4 — Relationship edges

- Ontology relationships (agent→district, claim→subject) remain knowledge/governance edges.  
- Authority edges (principal→agent, mandate→capability, revocation→subject) belong to ATG schemas + Identity Authority runtime.

---

## P1 — Federation sequencing

| Step | Owner | Status after this audit |
|---|---|---|
| SOVEREIGNTY identity audit | done | EMPTY-SHELL |
| ATG identity audit (PR #8 draft) | done / open | EMPTY-SHELL; not final registry |
| **ONTOLOGY identity audit (this PR)** | **done** | **EMPTY-SHELL** |
| PAY-PROTOCOL identity audit | **next (Codex/Cursor required)** | UNKNOWN |
| Assemble hub registry patch | `wiredchaos/agentropolis` | blocked on PAY + human apply |
| Designate/create Identity Authority | federation owners | blocked on audits |
| Implement runtime against ATG contracts | Identity Authority | after designation |
| ONTOLOGY entity schemas reference identity IDs | this repo | after ATG normative types exist |

---

## P2 — Documentation and README honesty

| ID | Action |
|---|---|
| D2-1 | README: state clearly that this repo is ontology/knowledge/money vocabulary, **not** identity authority or IdP |
| D2-2 | Point identity consumers to ATG (protocol) + dedicated Identity Authority (runtime) once designated |
| D2-3 | Mark research “Identity and wallets” row as non-canon radar |
| D2-4 | Cross-link this evidence pack from any future ontology principles doc |

---

## P2 — Test / validation (ontology scope only)

Add only when schemas expand:

- JSON Schema validation for money + future descriptive entities  
- Lint that identity foreign keys are present where SpendingAuthority / agent accountability is claimed  
- **Do not** add fake identity auth test suites that imply this repo enforces authN/authZ

---

## P3 — Cleanup

| ID | Action |
|---|---|
| C3-1 | Decide fate of unmerged structure + economic branches (merge with identity boundary notes, or archive) |
| C3-2 | Attach audit summary to federation Issue #85 when the hub repo is accessible (not fetchable here) |
| C3-3 | Keep proposed registry patch file in-repo as evidence; apply only via hub governance commit |

---

## Proposed registry patch

See `docs/audits/ONTOLOGY-IDENTITY-REGISTRY-PATCH.proposed.yaml`.

**Status:** PROPOSED ONLY — **not applied**.

### Acceptance criteria before applying

1. Human governance owner reviews EMPTY-SHELL identity status.  
2. ATG PR #8 and SOVEREIGNTY evidence are included in the **same** hub assembly (or explicitly sequenced commits).  
3. PAY-PROTOCOL audit completed or explicitly deferred with UNKNOWN status retained.  
4. Confirm no other repo is already CANONICAL for identity without code evidence.

---

## Recommended sequencing

```text
ONTOLOGY audit (this PR)
        ↓
AGENTROPOLIS-PAY-PROTOCOL audit
        ↓
Separate wallet/payment identity from root identity
        ↓
Assemble cross-repo registry patch in wiredchaos/agentropolis
  (SOVEREIGNTY + ATG + ONTOLOGY + PAY)
  — do not treat ATG PR #8 as final registry decision alone —
        ↓
DESIGNATE OR CREATE IDENTITY AUTHORITY
        ↓
Implement runtime against ATG normative contracts
        ↓
ONTOLOGY descriptive schemas reference identity IDs
```

---

## Out of scope for immediate patches

- Implementing identity runtime in this repository  
- Production authentication behavior changes  
- Auto-merging structure-branch schemas  
- Auto-applying federation registry  
- Marking this repository CANONICAL for identity  
- Merging ATG PR #8 as final registry decision

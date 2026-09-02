# ASR / ADR outline catalog — Agentic AI governance architecture

A title-only backlog, organized by architecture layer and cross-cutting concern. Each row is a placeholder for a future ASR or ADR — not yet drafted, not yet in the ASR/ADR Log. This catalog is the map; the Log is the territory once each entry is written and accepted.

See `Layer-Model.md` for the four-layer documentation model. Every ASR drafted from this catalog must carry a Layer-4 Family tag (AI, CLOUD, ON-PREM, or CROSS-CUTTING) in its Driver field, per the current ASR-Template.md, and should include a Corpus evidence section if a Layer-3 industry source genuinely corroborates it.

As of this backlog-drafting pass, 26 of 26 ASRs and 12 of 22 ADRs are **Drafted**. The remaining ADRs are **Proposed** — a title and nothing more, deliberately left undrafted where no genuine Layer-3 precedent existed to ground a decision on, rather than forced. One entry, ADR-003, is marked **Absorbed** — see "Using this catalog" below. Every row is ready to be picked up, split, merged, or dropped as the working group sees fit; a title here is a placeholder, not a commitment.

---

## 1. Autonomy & risk tiering
*Orchestrator layer — the control loop's decision authority*

| ID | Title | Status |
|---|---|---|
| ASR-001 | Governance model must support accelerated AI adoption without loss of risk management | Drafted |
| ASR-006 | Autonomy tier promotion requires independently measured accuracy, not elapsed time or output plausibility | Drafted |
| ASR-007 | A capability's autonomy tier must default to the lowest tier until explicitly raised | Drafted |
| ADR-001 | Autonomy is tiered per capability, from this point forward | Drafted |
| ADR-002 | Autonomy tier promotion and demotion process | Drafted |
| ADR-003 | Kill-switch / interrupt authority at defined checkpoints in an agent's action chain | Absorbed into ADR-019 |

## 2. Agent identity & access
*Cross-cutting — every layer an agent touches*

| ID | Title | Status |
|---|---|---|
| ASR-005 | Agent identity must be its own scoped entity, never inherited from an invoking user, service account, or integrated system | Drafted |
| ASR-008 | Agent credentials must be time-bounded and independently revocable from whatever provisioned them | Drafted |
| ASR-009 | Delegation from one agent to another must not silently expand the delegate's privilege beyond the delegator's scope | Drafted |
| ADR-004 | Agent identity provisioning and credential lifecycle pattern | Drafted |
| ADR-005 | Cross-mission-area agent sharing and delegation model | Drafted |

## 3. Guardrails & human oversight
*Guardrails layer — the boundary between agent internals and the external world*

| ID | Title | Status |
|---|---|---|
| ASR-003 | Agentic AI policy must specify architecture explicitly enough that written-policy compliance and architectural compliance cannot diverge | Drafted |
| ASR-010 | Automated guardrail checks must have their blind spots adversarially and periodically tested, not assumed safe from a clean pass rate | Drafted |
| ASR-011 | A human-approval checkpoint must be architecturally enforced by the orchestrator, not left to the underlying model's judgment | Drafted |
| ADR-006 | Guardrail and policy-enforcement control-point placement in the orchestration layer | Drafted |
| ADR-007 | Human-approval gate design for Tier 2 capabilities | Drafted |

## 4. Provenance & audit trail
*What every layer must leave behind for later inspection*

| ID | Title | Status |
|---|---|---|
| ASR-004 | Agent input-ingestion structural fidelity must be independently verified before autonomous authority is granted | Drafted |
| ASR-012 | Agent audit trails must preserve a layered, independently inspectable chain from source evidence to action | Drafted |
| ASR-013 | A break in the chain of custody must halt autonomous action; a disclosed, bounded quality miss must not | Drafted |
| ADR-008 | Audit-trail schema and logging architecture | Drafted |
| ADR-009 | Hard-stop vs. logged-limitation criteria for agent governance | Proposed |

## 5. Tools & resource governance
*Tools layer — what an agent can actually do to the world*

| ID | Title | Status |
|---|---|---|
| ASR-014 | Tool and capability access must be explicitly reviewed and approved per agent, not inherited from accumulated user or team access | Drafted |
| ASR-015 | Agent tasks must operate within defined ceilings on compute time, request rate, and data-store load | Drafted |
| ADR-010 | Tool and capability registry and approval workflow | Drafted |
| ADR-011 | Resource and consumption guardrails — rate limiting, cost and complexity ceilings | Proposed |

## 6. Memory & data governance
*Memory layer — short-term context and long-term recall*

| ID | Title | Status |
|---|---|---|
| ASR-016 | Long-term agent memory stores must be scoped and access-controlled with the same rigor as any other sensitive data store | Drafted |
| ASR-017 | Content an agent retrieves from memory must remain attributable to its originating session, never silently merged across users | Drafted |
| ADR-012 | Memory architecture and cross-session data isolation pattern | Proposed |

## 7. Model selection & evaluation
*Model layer — the reasoning engine itself*

| ID | Title | Status |
|---|---|---|
| ASR-018 | Model selection for a given capability must be justified by evaluated performance on that capability, not general benchmark reputation | Drafted |
| ADR-013 | Model selection and evaluation criteria, tiered by capability consequence | Proposed |

## 8. Policy coordination & ownership
*How this architecture stays connected to everything adjacent to it*

| ID | Title | Status |
|---|---|---|
| ASR-002 | Baseline governance directives must specify configuration-management and control-baseline requirements | Drafted |
| ASR-019 | Agentic AI policy must have an explicit, standing coordination mechanism to adjacent policy domains — Zero Trust, ICAM, data governance, procurement | Drafted |
| ADR-014 | Cross-domain policy coordination mechanism | Proposed |
| ADR-015 | Organizational ownership placement for agentic AI governance | Proposed |

## 9. Staged validation & trust
*What has to be proven before autonomy is extended*

| ID | Title | Status |
|---|---|---|
| ASR-020 | An agent must not be granted higher-order reasoning or action authority until the foundational layer it depends on has independently validated accuracy | Drafted |
| ASR-021 | An agent's self-reported confidence, accuracy, or completion status must never be the sole basis for trusting its output | Drafted |
| ADR-016 | Staged-validation gate model for autonomy grants | Drafted |
| ADR-017 | Independent recomputation and verification requirement for agent-reported claims | Drafted |

## 10. Vendor & system evaluation
*What gets checked before anything — built or bought — is authorized*

| ID | Title | Status |
|---|---|---|
| ASR-022 | Any agentic AI system, built internally or procured, must be evaluable against a standard set of governance questions before authorization | Drafted |
| ADR-018 | Adoption of the USDA agent developer / vendor evaluation checklist | Proposed |

## 11. Incident response & recovery
*What happens when a foundational assumption turns out to be wrong*

| ID | Title | Status |
|---|---|---|
| ASR-023 | A deprecated or invalidated agent architecture must be quarantined and retained for audit, not deleted | Drafted |
| ASR-024 | A systematic defect in an agent's foundational input pipeline must trigger rebuild from trusted source, not patching of downstream artifacts | Drafted |
| ADR-019 | Circuit-breaker and kill-switch architecture for autonomous workflows | Drafted |
| ADR-020 | Quarantine and clean-break remediation policy | Proposed |

## 12. Multi-agent coordination
*What changes when agents delegate to other agents*

| ID | Title | Status |
|---|---|---|
| ASR-025 | Delegation between agents must preserve autonomy tier and identity scoping across the delegation boundary | Drafted |
| ADR-021 | Multi-agent supervisor / delegate reference pattern | Drafted |

## 13. Lifecycle & change management
*How this architecture ages*

| ID | Title | Status |
|---|---|---|
| ASR-026 | Model and agent updates are configuration-managed changes requiring change-control documentation and regression testing against baseline behavior | Drafted |
| ADR-022 | Agent change-control, versioning, and authorizing-official notification policy | Proposed |

---

## Using this catalog

- **Drafted** entries are already written and in `ASR-Log.md` / `ADR-Log.md` — but every one of them carries a `Status` field of its own (currently `Draft` across the board), and that field, not this catalog, is the current word on where it stands. Read the document itself before treating it as settled.
- **Proposed** entries are titles only — claiming one means drafting the full ASR or ADR (using the templates) and moving it into the Log with a Status of its own, including a Family tag per Layer-Model.md.
- **Absorbed into ADR-YYY** means this entry's title described the same architectural decision as another catalog entry that was drafted under a different number — rather than draft a near-duplicate, the decision lives at ADR-YYY and this row stays in the catalog, marked accordingly, so the ID isn't silently dropped or reused.
- Numbering is sequential across the whole catalog, not per category, so an ID always identifies exactly one entry regardless of where it ends up living — including an absorbed one.
- This catalog itself is not authoritative — the Logs are. Treat this as a backlog to work from, not a commitment already made.

> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# Architecturally-Significant Requirements (ASR) Log

The index of all architecturally-significant requirements identified for the Agentic AI governance model. Each ASR states a requirement the architecture must satisfy, and traces to the ADR(s) that address it, if any exist yet. An ASR with no related ADR is an open requirement — a gap the library has surfaced but not yet resolved with a decision.

See `Layer-Model.md` for the four-layer documentation model and the definition of the Family tags below.

| ID | Title | Status | Date | Family | Related ADR(s) |
|---|---|---|---|---|---|
| ASR-001 | Governance model must support accelerated AI adoption without loss of risk management | Draft | 2026-08-31 | AI | ADR-001 |
| ASR-002 | Baseline governance directives must specify configuration-management and control-baseline requirements | Draft | 2026-08-31 | CROSS-CUTTING | None yet — open requirement |
| ASR-003 | Agentic AI policy must specify architecture explicitly enough that written-policy compliance and architectural compliance cannot diverge | Draft | 2026-08-31 | CROSS-CUTTING | None yet — open requirement |
| ASR-004 | Agent input-ingestion structural fidelity must be independently verified before autonomous authority is granted | Draft | 2026-08-31 | CROSS-CUTTING | None yet — open requirement |
| ASR-005 | Agent identity must be its own scoped entity, never inherited from an invoking user, service account, or integrated system | Draft | 2026-08-31 | CROSS-CUTTING | None yet — open requirement |
| ASR-006 | Autonomy tier promotion requires independently measured accuracy, not elapsed time or output plausibility | Draft | 2026-09-02 | AI, CROSS-CUTTING | ADR-002 |
| ASR-007 | A capability's autonomy tier must default to the lowest tier until explicitly raised | Draft | 2026-09-02 | CROSS-CUTTING | ADR-002 |
| ASR-008 | Agent credentials must be time-bounded and independently revocable from whatever provisioned them | Draft | 2026-09-02 | CROSS-CUTTING | ADR-004 |
| ASR-009 | Delegation from one agent to another must not silently expand the delegate's privilege beyond the delegator's scope | Draft | 2026-09-02 | CROSS-CUTTING | ADR-005 |
| ASR-010 | Automated guardrail checks must have their blind spots adversarially and periodically tested, not assumed safe from a clean pass rate | Draft | 2026-09-02 | CROSS-CUTTING | None yet — open requirement |
| ASR-011 | A human-approval checkpoint must be architecturally enforced by the orchestrator, not left to the underlying model's judgment | Draft | 2026-09-02 | CROSS-CUTTING | ADR-007 |
| ASR-012 | Agent audit trails must preserve a layered, independently inspectable chain from source evidence to action | Draft | 2026-09-02 | CROSS-CUTTING | ADR-008 |
| ASR-013 | A break in the chain of custody must halt autonomous action; a disclosed, bounded quality miss must not | Draft | 2026-09-02 | CROSS-CUTTING | None yet — open requirement |
| ASR-014 | Tool and capability access must be explicitly reviewed and approved per agent, not inherited from accumulated user or team access | Draft | 2026-09-02 | CROSS-CUTTING | ADR-010 |
| ASR-015 | Agent tasks must operate within defined ceilings on compute time, request rate, and data-store load | Draft | 2026-09-02 | CROSS-CUTTING | None yet — open requirement |
| ASR-016 | Long-term agent memory stores must be scoped and access-controlled with the same rigor as any other sensitive data store | Draft | 2026-09-02 | CROSS-CUTTING | None yet — open requirement |
| ASR-017 | Content an agent retrieves from memory must remain attributable to its originating session, never silently merged across users | Draft | 2026-09-02 | CROSS-CUTTING | None yet — open requirement |
| ASR-018 | Model selection for a given capability must be justified by evaluated performance on that capability, not general benchmark reputation | Draft | 2026-09-02 | AI | None yet — open requirement |
| ASR-019 | Agentic AI policy must have an explicit, standing coordination mechanism to adjacent policy domains — Zero Trust, ICAM, data governance, procurement | Draft | 2026-09-02 | CROSS-CUTTING | None yet — open requirement |
| ASR-020 | An agent must not be granted higher-order reasoning or action authority until the foundational layer it depends on has independently validated accuracy | Draft | 2026-09-02 | AI, CROSS-CUTTING | ADR-016 |
| ASR-021 | An agent's self-reported confidence, accuracy, or completion status must never be the sole basis for trusting its output | Draft | 2026-09-02 | AI | ADR-017 |
| ASR-022 | Any agentic AI system, built internally or procured, must be evaluable against a standard set of governance questions before authorization | Draft | 2026-09-02 | CROSS-CUTTING | None yet — open requirement |
| ASR-023 | A deprecated or invalidated agent architecture must be quarantined and retained for audit, not deleted | Draft | 2026-09-02 | CROSS-CUTTING | ADR-019 |
| ASR-024 | A systematic defect in an agent's foundational input pipeline must trigger rebuild from trusted source, not patching of downstream artifacts | Draft | 2026-09-02 | CROSS-CUTTING | None yet — open requirement |
| ASR-025 | Delegation between agents must preserve autonomy tier and identity scoping across the delegation boundary | Draft | 2026-09-02 | CROSS-CUTTING | ADR-021, ADR-005 |
| ASR-026 | Model and agent updates are configuration-managed changes requiring change-control documentation and regression testing against baseline behavior | Draft | 2026-09-02 | CROSS-CUTTING | None yet — open requirement |

New ASRs should be added to this table when accepted, in ID order. Do not delete a superseded ASR — mark it superseded and retain the row. Every new ASR must carry at least one Family tag (AI, CLOUD, ON-PREM, or CROSS-CUTTING) in both its Driver field and this table.

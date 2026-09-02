# Architecturally-Significant Requirements (ASR) Log

The index of all architecturally-significant requirements identified for the Agentic AI governance model. Each ASR states a requirement the architecture must satisfy, and traces to the ADR(s) that address it, if any exist yet. An ASR with no related ADR is an open requirement — a gap the library has surfaced but not yet resolved with a decision.

See `Layer-Model.md` for the four-layer documentation model and the definition of the Family tags below.

| ID | Title | Status | Date | Family | Related ADR(s) |
|---|---|---|---|---|---|
| ASR-001 | Governance model must support accelerated AI adoption without loss of risk management | Accepted | 2026-08-31 | AI | ADR-001 |
| ASR-002 | Baseline governance directives must specify configuration-management and control-baseline requirements | Accepted | 2026-08-31 | CROSS-CUTTING | None yet — open requirement |
| ASR-003 | Agentic AI policy must specify architecture explicitly enough that written-policy compliance and architectural compliance cannot diverge | Accepted | 2026-08-31 | CROSS-CUTTING | None yet — open requirement |
| ASR-004 | Agent input-ingestion structural fidelity must be independently verified before autonomous authority is granted | Accepted | 2026-08-31 | CROSS-CUTTING | None yet — open requirement |
| ASR-005 | Agent identity must be its own scoped entity, never inherited from an invoking user, service account, or integrated system | Accepted | 2026-08-31 | CROSS-CUTTING | None yet — open requirement |

New ASRs should be added to this table when accepted, in ID order. Do not delete a superseded ASR — mark it superseded and retain the row. Every new ASR must carry at least one Family tag (AI, CLOUD, ON-PREM, or CROSS-CUTTING) in both its Driver field and this table.

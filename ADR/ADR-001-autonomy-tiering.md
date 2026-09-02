> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ADR-001: Autonomy is tiered per capability, from this point forward

**Status:** Draft
**Date:** 2026-08-31
**Traces to:** ASR-001

## Context
Agentic systems combine an orchestrator, a model, memory, and tools into a loop that can take real action, not just produce text. Treating "autonomous" as a single binary state — either the system acts on its own or it doesn't — collapses decisions that carry very different risk profiles into one bucket. A system that drafts a report for human review and a system that executes irreversible financial transactions are both "agentic," but they should not be governed identically.

The traditional pre-production/production boundary also no longer reliably tracks risk for agentic architectures, because an agent with a given tool and data access behaves the same regardless of which environment label it's deployed under. Risk tracks *what the agent is permitted to do*, not *where it runs*.

## Policy context

Federal AI policy direction has shifted from a risk-averse default toward an accelerate-adoption posture, prioritizing innovation and public trust together rather than treating caution as the default setting. A governance model built around one department-wide dial — cautious or permissive — does not fit that shift well: setting the dial to "permissive" reads as abandoning risk management, and leaving it at "cautious" fails to reflect the new direction at all.

Tiering resolves this. Autonomy tiers assigned per capability, and calibrated against measured accuracy rather than institutional posture, allow the organization to move faster on well-validated, lower-consequence capabilities while continuing to apply the strongest controls to high-consequence ones. Risk management remains fully intact under this model — it simply operates per capability instead of uniformly across the organization. This ADR's tiering decision should be read as the structural mechanism that reconciles an accelerate-adoption policy direction with continued, defensible risk management, not as a relaxation of it.

## Decision
Autonomy will be assigned per capability, using a four-tier model, for every agentic capability designed or approved from this point forward:

| Tier | Description | Required control |
|---|---|---|
| 1 — Advisory only | Agent recommends; a human decides and acts | No direct system-action capability |
| 2 — Human-approved action | Agent proposes a specific action; a human approves before execution | Approval gate blocks execution until explicit sign-off |
| 3 — Bounded autonomous action | Agent acts without per-action approval, within an explicitly scoped, reversible action set | Scope enforced by the orchestrator, not by the model's judgment; actions logged and reversible |
| 4 — Full autonomy | Agent acts without per-action approval, including on irreversible or high-impact actions | Requires validated accuracy on the underlying capability, plus continuous monitoring and a kill-switch/interrupt path |

Tiering is assigned **per capability**, not per system or per environment. A single agent may hold Tier 1 for one capability (e.g., drafting a recommendation) and Tier 3 for another (e.g., querying a read-only data store), within the same deployment.

A capability's tier may only be raised, not assumed by default, and raising a tier requires the capability's underlying accuracy to be independently measured against a human-reviewed sample — not inferred from how plausible its output looks.

## Consequences
- Every new agentic capability design must state its tier explicitly before implementation, as part of its architecture documentation.
- Tier 4 capabilities require the strongest guardrail, identity-scoping, and audit-trail controls in the architecture; Tier 1 capabilities require the least, since a human remains the actor of record.
- This decision does not by itself define *which* tier any specific future capability should receive — that is a case-by-case risk determination made against this framework, not a blanket default.
- This decision supersedes any prior assumption that "agentic" implies a single, uniform level of autonomous action across a system.

## Amendment log
- 2026-08-31 — Initial version.
- 2026-08-31 — Added Policy context section addressing the shift from a risk-averse to an accelerate-adoption federal AI policy posture.
- 2026-08-31 — Added ASR traceability header; this ADR now formally traces to ASR-001 in the ASR Log.
- 2026-08-31 — Aligned to the four-layer documentation model (see Layer-Model.md); ASR-001's Driver now carries the [AI] family tag. No change to the decision itself.
- 2026-09-02 — Status corrected from Accepted to Draft. No Layer 1 authorizing instrument has signed off on this decision yet; "Accepted" in the Status field is reserved for that, per Layer-Model.md's directionality (Layer 2 compiles into Layer 1 once mature and accepted). No change to the decision itself.
- 2026-09-02 — Title corrected from "Autonomy is tiered, effective from this point forward" to "Autonomy is tiered per capability, from this point forward," to match the wording already used in ADR-Log.md and ASR-ADR-Outline-Catalog.md since this ADR was first logged — a wording drift, not a change of decision; treated as non-substantive per CONTRIBUTING.md's own carve-out for markdown-link-level fixes.

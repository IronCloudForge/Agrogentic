> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-025: Delegation between agents must preserve autonomy tier and identity scoping across the delegation boundary

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-53 Rev 5 (AC-6 least privilege); SP 800-207 (Zero Trust) — the same driver family as ASR-009, applied here to autonomy tier rather than privilege scope alone

## Requirement statement
When one agent delegates a task to another, the delegate's autonomy tier for executing that task must not exceed the lower of the delegator's own tier for that capability and the delegate's own independently granted tier for it (per ADR-002). The delegate's identity scoping (per ASR-005 and ASR-009) must remain intact through the delegation — it must never collapse into the delegator's identity for the duration of the delegated task.

## Architectural significance
Without this preservation requirement, delegation could function as a tier-laundering path: a Tier 1 capability delegating to an agent independently authorized at Tier 3 for a superficially similar task could end up executing with more autonomy than either agent's own governance history actually supports. The identity boundary ASR-005 requires is also most likely to be overlooked in review specifically at a delegation handoff, which is why this requirement states the preservation explicitly rather than assuming ASR-005 and ADR-002 already cover it by implication.

## Corpus evidence
An open-source agent-governance toolkit's delegation-chain conformance suite (135 tests, AgentMesh Identity and Trust specification) formally verifies delegation behavior as its own tested concern, distinct from either agent's standalone identity or tier — evidence that delegation-boundary preservation is treated, in working reference implementations, as requiring its own explicit verification rather than being assumed from each agent's individual governance (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit).

## Related ADRs
ADR-021 (multi-agent supervisor/delegate reference pattern) addresses the tier-preservation half of this requirement; ADR-005 (cross-mission-area sharing and delegation) addresses the identity-scoping half.

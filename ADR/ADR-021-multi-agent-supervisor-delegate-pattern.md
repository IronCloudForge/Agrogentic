> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ADR-021: Multi-agent supervisor / delegate reference pattern

**Status:** Draft
**Date:** 2026-09-02
**Traces to:** ASR-025

## Context
ASR-025 requires that delegation between agents preserve autonomy tier and identity scoping across the delegation boundary. This decision defines the reference pattern for how a supervising agent and its delegates relate structurally.

## Decision
- A supervising agent that delegates tasks to other agents does not delegate its own autonomy tier wholesale; each delegated task carries its own tier determination, computed as the lower of the supervisor's tier for that capability and the delegate's own independently granted tier for it (per ASR-025).
- The delegate's identity remains its own scoped entity throughout the delegation (per ASR-005) — the supervisor's identity is never substituted for the delegate's when the delegate acts, even though the supervisor initiated the task.
- The supervisor logs the delegation decision itself (the choice to delegate, and to which agent) in its own audit trail (per ADR-008); the delegate logs its own execution of the delegated task in its own audit trail. Neither substitutes for the other.
- A delegation chain has a defined maximum depth; a delegate may not itself delegate further without that additional hop being subject to the same tier-and-identity preservation rule, recursively.

## Corpus reference
An open-source agent-governance toolkit's Agent Mesh package implements agent discovery, routing, and a cross-agent trust mesh as working infrastructure, backed by delegation-chain conformance testing (135 tests, AgentMesh Identity and Trust) and peer trust negotiation (62 tests, AgentMesh Trust and Coordination) (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit). Cited as precedent that a structured supervisor/delegate mesh with bounded, tested delegation chains is a buildable pattern, not as authority for this specific reference pattern.

## Consequences
- Gives ASR-025 a concrete structural pattern.
- Directly builds on ADR-005 (cross-mission-area sharing) — this pattern applies within a single mission area as well as across the boundary ADR-005 addresses.
- Does not itself set the maximum delegation-chain depth — left as an implementation parameter.

## Amendment log
- 2026-09-02 — Initial version.

> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ADR-005: Cross-mission-area agent sharing and delegation model

**Status:** Draft
**Date:** 2026-09-02
**Traces to:** ASR-005, ASR-009

## Context
Agents built for one mission area or system may be reused, invoked, or delegated to by another. ASR-005 requires agent identity to remain its own scoped entity across every system it touches; ASR-009 requires that delegation between agents never silently expand a delegate's privilege beyond its delegator's scope. Absent an explicit model, cross-mission-area sharing defaults to whatever the least well-governed integration point allows — the outcome ASR-005 was written to prevent, reproduced at the delegation boundary rather than the identity boundary.

## Decision
Cross-mission-area agent sharing and delegation follows an explicit, bounded-trust model rather than an open mesh:

1. An agent's identity credential is scoped to the mission area that provisioned it and does not automatically carry across mission-area boundaries.
2. Delegation to an agent in a different mission area requires an explicit, recorded trust relationship between the two mission areas' agent registries — never an implicit inference from shared network or shared infrastructure.
3. A delegate agent's effective scope for a delegated task is the intersection of its own provisioned scope and the scope the delegator explicitly passed — never the delegate's full native scope.
4. Every cross-mission-area delegation is logged with both agents' identities and the scope passed, independent of either mission area's own internal logging.

## Corpus reference
An open-source agent-governance toolkit's Agent Mesh package is built specifically for agent discovery, routing, and a cross-agent trust mesh, backed by a 62-test AgentMesh Trust and Coordination specification covering peer trust negotiation and mesh-wide policy (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit). Cited as precedent that a bounded, explicitly-negotiated trust mesh between agents from different origins is a buildable pattern, not as authority for this specific model.

## Consequences
- Gives ASR-009 an enforceable mechanism at the specific point — cross-mission-area sharing — where delegation risk is highest.
- Does not itself define which mission areas are authorized to establish a trust relationship with which others — an organizational-ownership decision deferred to ADR-015 (backlog, currently undrafted).
- Interacts directly with ADR-002 (autonomy tier promotion): a delegated task inherits the delegate's own autonomy tier for the capability being invoked, not the delegator's.

## Amendment log
- 2026-09-02 — Initial version.

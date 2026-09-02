> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ADR-007: Human-approval gate design for Tier 2 capabilities

**Status:** Draft
**Date:** 2026-09-02
**Traces to:** ASR-011

## Context
ADR-001 defines Tier 2 (human-approved action) as requiring an approval gate that blocks execution until explicit sign-off. ASR-011 requires that gate to be architecturally enforced. ADR-006 places the enforcement point in the orchestrator generally; this decision defines what the Tier 2 approval gate itself looks like at that point.

## Decision
A Tier 2 capability's proposed action is held by the orchestrator's control point (per ADR-006) in a require-approval state until an explicit, attributable approval is recorded. The action does not execute on timeout, on approval-request delivery failure, or on any other absence of an explicit response — absence of response is treated as no approval, never as implicit approval. Each approval request presents the specific action to be taken, not a session-level or batched summary covering multiple actions, so that approval fatigue from reviewing unrelated prior actions cannot substitute for review of the action actually being approved. Each approval is recorded with the identity of the human approver, the action approved, and the timestamp, as part of the audit trail (see ADR-008).

## Corpus reference
An open-source agent-governance toolkit implements a directly comparable pattern in its policy engine — a `require_approval` action type naming specific approvers, evaluated per action rather than per session (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit). Production deployment findings are cited here as a cautionary counter-example rather than a positive precedent: batched, high-volume approval flows in practice produced "approval fatigue," with users approving 50 or more actions per session without meaningful review — the specific failure mode this decision's per-action, non-batched design is intended to avoid (Uber ADR, MLSys 2026 Industry Track slides; mlsys.org/media/mlsys-2026/Slides/3853_k9cXWDE.pdf).

## Consequences
- Makes Tier 2's "human approves before execution" control (ADR-001) concrete and testable.
- Does not itself define who is authorized to serve as an approver for a given capability — an organizational-ownership question deferred to ADR-015 (backlog, currently undrafted).
- A future capability-specific ADR should assume this per-action, non-implicit-approval design rather than re-derive it.

## Amendment log
- 2026-09-02 — Initial version.

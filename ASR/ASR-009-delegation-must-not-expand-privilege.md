> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-009: Delegation from one agent to another must not silently expand the delegate's privilege beyond the delegator's scope

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-53 Rev 5 least-privilege principle (AC-6), generalized to agent-to-agent delegation; SP 800-207 (Zero Trust — per-transaction verification, not inherited trust)

## Requirement statement
When one agent delegates a task to another agent, the delegate must never hold, as a result of that delegation, greater privilege or broader scope than the delegator itself held. A delegation chain must be explicitly bounded at each hop, not accumulated implicitly.

## Architectural significance
Multi-agent systems that do not enforce this bound allow privilege to expand as tasks pass between agents. A delegate operating with broader scope than its delegator defeats the same minimum-necessary-access principle ASR-005 establishes for a single agent's identity, at the specific boundary — between agents — where a single-agent scoping model does not automatically apply. Without an explicit, enforced bound at each delegation hop, a multi-agent chain's effective privilege is set by whichever hop was least carefully scoped, not by the task's actual requirements.

## Corpus evidence
An open-source agent-governance toolkit's identity and trust layer formally specifies delegation chains as part of its AgentMesh Identity and Trust conformance suite (135 tests), and its architecture is built specifically to intercept delegation events — "every tool call, message send, and delegation" — in deterministic policy code before an agent's request reaches another agent (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit).

## Related ADRs
ADR-005 (cross-mission-area agent sharing and delegation model) addresses this requirement directly.

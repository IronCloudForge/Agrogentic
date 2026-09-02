> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-008: Agent credentials must be time-bounded and independently revocable from whatever provisioned them

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-53 Rev 5 (IA-5 authenticator management; AC-2 account management, generalized to non-human/agent credentials); SP 800-207 (Zero Trust — continuous verification, not standing trust)

## Requirement statement
Every credential issued to an agent must carry an explicit, bounded expiration and must be revocable independently of the system, service, or process that originally provisioned it. Revocation must not require disabling or modifying the provisioning system itself.

## Architectural significance
Without independent revocability, revoking a single compromised or misbehaving agent's access requires touching whatever provisioned it — collapsing the agent-identity boundary ASR-005 establishes back into whatever system issued the credential in the first place. Standing, non-expiring credentials compound this: an agent credential that never expires remains valid for as long as it goes unnoticed, regardless of whether the agent, its task, or its authorization still exists.

## Corpus evidence
An open-source agent-governance toolkit issues per-agent identity credentials as a first-class part of its architecture — SPIFFE/DID-based, distinct from any invoking user or service account — with credential and trust-scoring behavior covered by its own 135-test formal specification (AgentMesh Identity and Trust), demonstrating that agent-scoped, independently manageable credentials are a working, testable pattern rather than a theoretical requirement (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit). A production enterprise agent-security system separately treats credential exposure as its single most consequential finding category, flagging 206 true-positive credential exposures across 26 categories in deployment — underscoring that credential lifecycle discipline is a live operational concern once agents operate at scale, not a hypothetical one (Uber ADR, MLSys 2026 Industry Track paper; arXiv:2605.17380).

## Related ADRs
ADR-004 (agent identity provisioning and credential lifecycle pattern) addresses this requirement directly.

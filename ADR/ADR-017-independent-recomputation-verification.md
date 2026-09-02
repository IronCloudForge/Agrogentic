> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ADR-017: Independent recomputation and verification requirement for agent-reported claims

**Status:** Draft
**Date:** 2026-09-02
**Traces to:** ASR-021

## Context
ASR-021 requires that an agent's self-reported confidence, accuracy, or completion status never be the sole basis for trusting its output. This decision defines how independent verification is structured.

## Decision
- Any claim an agent makes about its own output — confidence, correctness, or completion — is checked against an independent source before that claim is relied upon for a governance decision: a tier promotion (ADR-002), an audit record (ADR-008), or a policy verdict (ADR-006).
- "Independent" means the verification does not rely on the same model, the same reasoning pass, or the same session that produced the original claim.
- Where independent recomputation is possible — a deterministic calculation, a retrievable fact — the architecture recomputes rather than accepting the agent's stated result.
- Where recomputation is not possible — a judgment call — the architecture requires an independent reviewer, human or a separate detection system, rather than accepting the agent's own confidence score as sufficient.

## Corpus reference
A production enterprise agent-security system is built entirely around this principle in practice: rather than relying on any signal the monitored agent itself reports, it operates as a wholly independent detection layer, evaluating agent behavior externally against its own detectors, threat intelligence, and policy checks (Uber ADR, MLSys 2026 Industry Track paper; arXiv:2605.17380). A separate open-source governance toolkit frames its audit function around the same question from the auditor's side — "can you prove what happened?" — with tamper-evident records designed to be checked independent of the agent's own account (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit).

## Consequences
- Gives ASR-021 a concrete mechanism.
- Directly depends on ADR-008's audit schema existing as the independent record claims are checked against.
- Does not itself define which specific claims require recomputation versus independent human review — a case-by-case determination left to implementation.

## Amendment log
- 2026-09-02 — Initial version.

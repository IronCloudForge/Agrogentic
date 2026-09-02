> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-010: Automated guardrail checks must have their blind spots adversarially and periodically tested, not assumed safe from a clean pass rate

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-53 Rev 5 (CA-8 penetration testing; RA-5 vulnerability monitoring, generalized to agentic guardrail testing); SP 800-137 (continuous monitoring principle)

## Requirement statement
Automated guardrail and detection controls governing agentic capabilities must be periodically tested by adversarial, red-team-style probing designed to find their blind spots — not evaluated solely by the rate at which they pass routine or previously-seen cases. A guardrail's coverage must be measured category by category, not summarized as a single aggregate pass rate.

## Architectural significance
An aggregate pass rate can be high while specific categories of failure remain severely under-detected, and a guardrail tested only against the cases it was built to catch will reliably appear safe regardless of what it actually misses. Without periodic adversarial testing aimed at finding blind spots, a guardrail's apparent reliability reflects the thoroughness of its original test set, not its actual coverage against inputs designed to evade it.

## Corpus evidence
A production enterprise agent-security system's own benchmark results show exactly this pattern: overall detection performance is strong (F1 0.800, best-in-class among baselines), yet one specific threat category — Permission Abuse — is detected at only 20%, a gap invisible in the aggregate score and surfaced only because the evaluating benchmark broke results out by category (Uber ADR, MLSys 2026 Industry Track paper; arXiv:2605.17380). The same system includes a dedicated offline adversarial-discovery component — three collaborative red-teaming, evaluation, and threat-intelligence agents running an evolutionary search specifically to surface variants the detector currently misses — built as a standing part of the system rather than a one-time pre-launch exercise (Uber ADR, MLSys 2026 Industry Track paper; arXiv:2605.17380). A separate open-source governance toolkit ships adversarial red-teaming as a first-class, repeatable operation against an agent's own guardrails — a 12-vector prompt-injection audit CLI tool — rather than a one-time certification step (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit).

## Related ADRs
None yet — open requirement.

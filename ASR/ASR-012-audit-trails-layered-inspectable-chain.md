> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-012: Agent audit trails must preserve a layered, independently inspectable chain from source evidence to action

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-53 Rev 5 (AU-3 content of audit records; AU-9 protection of audit information, generalized to agentic action logging); SP 800-207 (Zero Trust — continuous, verifiable logging as a control, not a byproduct)

## Requirement statement
Every action an agent takes must be traceable through a layered audit record connecting the action back to the input, reasoning step, and authorization that produced it, in a form an independent reviewer — not the agent, and not the system that executed the action — can inspect without needing to reconstruct the chain from application logs never designed for that purpose.

## Architectural significance
An agentic system that logs only its final outputs, or logs incidental application events not designed to reconstruct causality, cannot support after-the-fact review of why a given action occurred — a reviewer investigating an unexpected or harmful action has no way to distinguish a reasoning failure, a tool-input failure, or a policy-enforcement failure from the log alone. Without a layered, purpose-built chain, the audit trail's completeness depends on whatever incidental logging happened to exist, not on a designed guarantee that the full path from evidence to action is reconstructable.

## Corpus evidence
A production enterprise agent-security system's observability component is built specifically to reconstruct "the full causal chain of agentic activity — user prompts, agent reasoning, MCP tool invocations (arguments and results), and environmental context" as a dedicated layer, rather than deriving this from general application logs (Uber ADR, MLSys 2026 Industry Track paper; arXiv:2605.17380). A separate open-source governance toolkit implements a tamper-evident audit layer with a formally specified schema — a 157-test Audit and Compliance specification covering Merkle-tree audit records and a per-decision "Decision BOM" — built as the system's audit-of-record rather than an incidental log stream (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit).

## Related ADRs
ADR-008 (audit-trail schema and logging architecture) addresses this requirement directly.

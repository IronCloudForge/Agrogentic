> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ADR-008: Audit-trail schema and logging architecture

**Status:** Draft
**Date:** 2026-09-02
**Traces to:** ASR-012

## Context
ASR-012 requires a layered, independently inspectable audit chain from source evidence to action. This decision defines the schema and architecture that satisfies it.

## Decision
| Layer | Content | Independent of |
|---|---|---|
| Evidence | The source input(s) the action was based on, with provenance per ASR-004 | The agent's own reasoning output |
| Reasoning | The agent's decision trace connecting evidence to the proposed action | The tool-execution layer |
| Authorization | The policy verdict and, where applicable, the human approval record (per ADR-007) that permitted execution | The action's own success or failure |
| Action | The action actually executed, including its result | The agent's own self-report of what it did |

Each layer is recorded independently and is queryable on its own — a reviewer must be able to inspect the authorization record without needing the reasoning trace to have also been captured correctly, and vice versa. Records are tamper-evident once written (append-only, with integrity verification), and retained for a defined minimum period independent of the system that generated them.

## Corpus reference
An open-source agent-governance toolkit implements a structurally comparable four-part flow — Agent → Policy Engine → Identity → Audit Log, with tamper-evident, Merkle-tree-based audit records and a per-decision "Decision BOM," backed by a 157-test formal specification — as a working reference architecture (Microsoft Agent Governance Toolkit, Audit and Compliance specification; github.com/microsoft/agent-governance-toolkit). A production agentic-security system separately demonstrates the evidence/reasoning/action layering in practice, reconstructing prompts, reasoning, and tool invocations as distinct, separately inspectable elements of its causal-chain observability layer (Uber ADR, MLSys 2026 Industry Track paper; arXiv:2605.17380).

## Consequences
- Gives ASR-012 a concrete schema.
- The retention period and specific tamper-evidence mechanism (e.g., Merkle tree versus another approach) are left as implementation choices, not fixed by this decision.
- This schema is the dependency ADR-002's Step 4/5 grant-and-demotion records, and ADR-007's approval records, both presume exists.

## Amendment log
- 2026-09-02 — Initial version.

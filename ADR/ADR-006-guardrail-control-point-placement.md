> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ADR-006: Guardrail and policy-enforcement control-point placement in the orchestration layer

**Status:** Draft
**Date:** 2026-09-02
**Traces to:** ASR-003, ASR-011

## Context
ASR-003 requires architectural compliance to be inseparable from written-policy compliance; ASR-011 requires human-approval checkpoints to be architecturally enforced rather than left to model judgment. Both require guardrail and policy checks to sit at a specific, defined point in the orchestration flow — not distributed inconsistently across prompt instructions, application code, and ad hoc checks wherever a developer happened to add one.

## Decision
Guardrail and policy-enforcement checks are placed as a mandatory interception point in the orchestrator, positioned between an agent's decision to act (a tool call, a message send, a delegation) and that action's actual execution — never after execution, and never solely inside the model's own generation step. Every such action passes through this single control point regardless of which capability, tier, or agent originated it; the check evaluates the requested action against the active policy and returns an explicit allow, deny, or require-approval verdict before execution is permitted to proceed. A denied or gated action fails closed: absent an explicit allow verdict, the action does not execute.

## Corpus reference
An open-source agent-governance toolkit implements exactly this control-point placement as its architecture — Agent → Policy Engine → Identity → Audit Log, with every tool call, message send, and delegation intercepted in deterministic policy code (YAML/OPA/Cedar-based) before reaching the wire — backed by a formally specified, fail-closed policy decision runtime (Microsoft Agent Governance Toolkit, Agent Control Specification; github.com/microsoft/agent-governance-toolkit). Cited as precedent that this placement is implementable as a stateless, deterministic interception layer, not as authority for the specific policy language or rule set to adopt.

## Consequences
- Gives ASR-011 (and, by extension, ASR-003) a concrete architectural location rather than a general principle.
- Requires that every orchestrator implementation in scope expose a single, auditable interception point for this purpose — an orchestrator design that cannot support this placement does not satisfy ASR-011 regardless of what guardrails it claims elsewhere.
- Does not itself specify the policy language, rule format, or specific rule set to enforce at this control point — left to implementation.
- Directly enables ADR-007's approval-gate design, which assumes this control point already exists.

## Amendment log
- 2026-09-02 — Initial version.

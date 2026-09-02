> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ADR-016: Staged-validation gate model for autonomy grants

**Status:** Draft
**Date:** 2026-09-02
**Traces to:** ASR-020

## Context
ASR-020 requires that a capability not be granted higher-order reasoning or action authority until the foundational layer it depends on has independently validated accuracy. ADR-002 already defines the promotion/demotion process for a single capability's own autonomy tier. This decision addresses a distinct but related concern: validating each architectural layer — model, identity/credentialing, guardrails, audit — before anything built on top of it is trusted, independent of any single capability's own tier history.

## Decision
| Layer | Gate before dependents may rely on it |
|---|---|
| Model | Independently measured accuracy on the specific capability, per ASR-006 and ASR-018 — not general benchmark reputation. |
| Identity / credentialing | Conformance-tested against its formal specification (per ADR-004) before any capability is permitted to rely on it for scoping. |
| Guardrails / policy enforcement | Adversarially tested per ASR-010 before being relied upon as the sole control at a Tier 3+ capability's control point. |
| Audit trail | Schema and integrity verified (per ADR-008) before being relied upon as evidence for a promotion decision (per ADR-002). |

A capability may not be promoted past Tier 1 under ADR-002 if any layer it depends on has not cleared its own gate — a capability's own accuracy measurement does not substitute for the foundational layers beneath it also having been independently validated.

## Corpus reference
An independent agent-governance specification gates promotion on demonstrated trustworthiness against defined maturity levels rather than default assumption (Agentic Trust Framework v0.9.1; github.com/massivescale-ai/agentic-trust-framework). A separate open-source governance toolkit gates its own components behind 992 conformance tests across 10 formal specifications — one per architectural layer — before a layer is treated as production-ready by anything depending on it (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit). Cited as precedent that layer-gated validation, distinct from single-capability promotion, is a buildable and already-adopted pattern.

## Consequences
- Extends ADR-002 rather than replacing it: ADR-002 governs a single capability's own tier; this decision governs whether the layers underneath any capability have been validated at all.
- Does not itself define the specific accuracy threshold or conformance-test count required per layer — left as implementation-specific.
- Directly depends on ADR-004 (identity) and ADR-008 (audit) already being in place as two of the layers it gates.

## Amendment log
- 2026-09-02 — Initial version.

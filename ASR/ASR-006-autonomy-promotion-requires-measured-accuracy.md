> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-006: Autonomy tier promotion requires independently measured accuracy, not elapsed time or output plausibility

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: AI, CROSS-CUTTING] NIST AI RMF (Measure function — assessing AI system trustworthiness characteristics with defined metrics); SP 800-137 (continuous, evidence-based monitoring principle, generalized to autonomy-tier review)

## Requirement statement
A capability's autonomy tier may be raised only on the basis of accuracy independently measured against a human-reviewed, production-representative sample of that capability's own output, evaluated against a threshold defined before the measurement is taken. Elapsed time operating at a lower tier, the absence of a reported incident, or the subjective plausibility of the agent's output must never, by themselves, justify a tier promotion.

## Architectural significance
Without an independent measurement requirement, promotion decisions default to whichever signal is easiest to observe — how long a capability has run without complaint, or how convincing its output reads to a reviewer — and neither is evidence of underlying accuracy. Absence of a reported incident is not evidence of correctness when the human review step is itself the control expected to catch errors and is demonstrably prone to under-scrutinizing high-volume, repetitive approvals. A promotion path that can be satisfied by plausible-looking output, rather than a measured result, lets a capability accumulate real-world authority at exactly the checkpoint the architecture places to prevent that from happening on appearance alone.

## Corpus evidence
Uber's own deployment findings, presented alongside its production detection system, describe an "approval fatigue" pattern in which users approve 50 or more agent actions per session without meaningful review — reported as "YOLO mode" usage without sandboxing, and noted as producing no real human oversight in practice despite an approval step nominally being in place (Uber ADR, MLSys 2026 Industry Track slides; mlsys.org/media/mlsys-2026/Slides/3853_k9cXWDE.pdf). The same system's own measured detection rates vary sharply by threat category on identical evaluation methodology — from 100% down to 20% for Permission Abuse — demonstrating that a capability's apparent reliability is not uniform across what it actually does, and that only a category-specific measurement, not an overall impression of the system, reveals where it is weak (Uber ADR, MLSys 2026 Industry Track paper; arXiv:2605.17380). An independent agent-governance specification's maturity model states its promotion principle directly: agents earn autonomy "through demonstrated trustworthiness — not by default" against defined promotion gates, with immediate demotion on a critical incident regardless of how long a tier had been held (Agentic Trust Framework v0.9.1; github.com/massivescale-ai/agentic-trust-framework).

## Related ADRs
ADR-002 (autonomy tier promotion and demotion process) defines the measurement and review mechanics this requirement calls for.

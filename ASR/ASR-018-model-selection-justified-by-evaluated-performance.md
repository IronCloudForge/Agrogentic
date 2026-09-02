> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-018: Model selection for a given capability must be justified by evaluated performance on that capability, not general benchmark reputation

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: AI] NIST AI RMF (Measure function — assessing AI system performance against its actual intended use, not a general reputation)

## Requirement statement
The model selected to power a given agentic capability must be justified by that model's evaluated performance on that specific capability's own task and data distribution. General benchmark reputation, popularity, or performance on unrelated tasks must not by itself justify the selection.

## Architectural significance
A model's strong general-purpose reputation does not guarantee it performs well on any specific downstream capability — the same divergence ASR-006 identifies between aggregate reliability and category-specific weakness applies equally to model selection. Without a capability-specific evaluation requirement, model selection defaults to reputation as a proxy for suitability, and a capability can be built on a model that is well-regarded in general but has never actually been measured against the task it is being assigned.

## Corpus evidence
A production enterprise agent-security system's own published results illustrate this divergence directly: strong aggregate performance (F1 0.800, best among baselines) coexists with a single category — Permission Abuse — detected at only 20%, a gap an aggregate reputation score would never surface (Uber ADR, MLSys 2026 Industry Track paper; arXiv:2605.17380). The same evidence used in ASR-006 for autonomy-tier promotion applies here to a different decision — model selection — precisely because it demonstrates the same underlying principle: aggregate performance and task-specific performance are not interchangeable measurements.

## Related ADRs
None yet — open requirement. (ADR-013, the model-selection and evaluation criteria decision this requirement calls for, remains undrafted pending clearer corpus precedent; see `ASR-ADR-Outline-Catalog.md`.)

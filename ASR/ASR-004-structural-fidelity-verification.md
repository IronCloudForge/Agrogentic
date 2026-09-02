# ASR-004: Agent input-ingestion structural fidelity must be independently verified before autonomous authority is granted

**Status:** Accepted
**Date:** 2026-08-31
**Driver:** [Family: CROSS-CUTTING] General data-provenance and quality-assurance principles; applies to any document-ingesting agentic capability

## Requirement statement
Any agent that ingests, parses, chunks, or retrieves source documents before reasoning over them must have the structural fidelity of that ingestion independently verified — through measured accuracy against a human-reviewed sample, not through output plausibility — before the agent is granted autonomous authority to act on its interpretation of that content.

## Architectural significance
A document-ingestion or chunking pipeline can silently drop or corrupt structurally significant content — a clause, a table row, a nested requirement, an inherited obligation spanning a chunk boundary — while still producing output that looks complete, coherent, and well-formatted. This is a defect class defined by producing plausible output; it is not detectable by the agent's own confidence signal, and it is not reliably detectable by a human reviewing only the output rather than the source. An agentic governance model that calibrates autonomy authority against how correct an agent's output *looks* is measuring the wrong thing, and will grant autonomy to capabilities whose actual input-fidelity has never been checked.

## Corpus evidence
A production enterprise agentic-security system's own ablation study found that removing source-code inspection from its verification context — one specific input-fidelity check — dropped detection recall by roughly 14% relative and F1-score by over 15%, a direct, measured demonstration that verification-context completeness materially changes correctness rather than merely refining an already-plausible output (Uber ADR, MLSys 2026 Industry Track; arXiv:2605.17380). Independent research into automated scanning of agent-facing content has separately found that pattern-matching-based scanners are structurally unable to detect the majority of critical issues, because the attacks that matter rely on natural-language instruction manipulation rather than signatures a scanner can pattern-match against — corroborating that plausibility-based or shallow-scan verification is not a substitute for measured, structure-aware review (Snyk, "Why Your Skill Scanner Is Just False Security," Feb 2026; cited in OWASP Agentic Skills Top 10, github.com/OWASP/www-project-agentic-skills-top-10).

## Related ADRs
None yet — open requirement.

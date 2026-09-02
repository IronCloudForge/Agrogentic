> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-002: Baseline governance directives must specify configuration-management and control-baseline requirements

**Status:** Draft
**Date:** 2026-08-31
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-53 Rev 5 control families; NIST SP 800-128 (configuration management / CI schema)

## Requirement statement
Any directive or policy document that establishes an agent's authorization boundary must explicitly define configuration-management requirements, a change-control process, and a control baseline for that boundary. An agentic system's governance cannot be more rigorous than the least specific directive it inherits its authorization boundary from.

## Architectural significance
When a baseline directive omits an explicit configuration-management requirement, a change-control board reference, or a defined control hierarchy, any system authorized under that directive inherits the ambiguity by default — including an agentic system capable of modifying its own behavior or configuration at machine speed. This gap is not visible from the directive's text alone; it only becomes visible when someone attempts to trace a specific control requirement back to its source and finds no requirement to trace. An agentic governance model that assumes baseline directives are complete, without verifying that CM and control-baseline requirements are explicitly present, inherits this gap silently.

## Corpus evidence
A MITRE work product built specifically to close this class of gap for AI systems demonstrates the level of specificity this requirement calls for: it maps AI-specific threat techniques directly onto roughly 100 individual NIST SP 800-53 Rev 5 controls, rather than citing the control catalog as a whole, and supplies assessor interview question sets so a control-baseline gap is discoverable during an assessment rather than only after an incident (MITRE, "SAFE-AI: A Framework for Securing AI-Enabled Systems"; atlas.mitre.org).

## Related ADRs
None yet — open requirement.

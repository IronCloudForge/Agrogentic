> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-023: A deprecated or invalidated agent architecture must be quarantined and retained for audit, not deleted

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-53 Rev 5 (AU-11 audit record retention, generalized to deprecated architecture retention); general forensic/audit-integrity principle

## Requirement statement
When an agent architecture, capability, or configuration is deprecated or found invalid, it must be quarantined — isolated from active use but retained in a form available for audit — rather than deleted.

## Architectural significance
Deletion destroys the evidentiary record needed to understand why an architecture was invalidated, whether it produced any downstream effects before deprecation, and whether a later architecture shares its flawed assumptions. Without a quarantine requirement, the default incentive after finding a problem is to remove the evidence of it along with the problem itself — foreclosing exactly the retrospective review ASR-012's audit-chain requirement exists to support.

## Related ADRs
None yet — open requirement. (ADR-020, the quarantine and clean-break remediation policy this requirement calls for, remains undrafted pending clearer corpus precedent.)

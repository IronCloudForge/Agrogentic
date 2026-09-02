> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ASR-026: Model and agent updates are configuration-managed changes requiring change-control documentation and regression testing against baseline behavior

**Status:** Draft
**Date:** 2026-09-02
**Driver:** [Family: CROSS-CUTTING] NIST SP 800-53 Rev 5 (CM-3 configuration change control); SP 800-128 (configuration management) — directly extending ASR-002's baseline-directive requirement to the update/change lifecycle

## Requirement statement
Any change to a model or agent already in production — a model version update, a prompt or policy change, a tool registration change — is a configuration-managed change requiring documented change-control review and regression testing against the capability's established baseline behavior before deployment. A model or agent update must never be treated as exempt from configuration management on the basis that it originates from a vendor-side update rather than an internal code change.

## Architectural significance
Model and agent updates can silently change a capability's behavior without any corresponding code change on the deploying organization's side — a vendor-side model update can alter behavior as materially as an internal change would, yet falls outside change-control discipline unless explicitly brought into scope. Without regression testing against baseline behavior specifically, a capability's autonomy tier — granted under ADR-002 against a specific measured accuracy — could continue to apply to a materially different underlying model that was never re-measured against that grant.

## Related ADRs
None yet — open requirement. (ADR-022, the change-control, versioning, and authorizing-official notification policy this requirement calls for, remains undrafted pending clearer corpus precedent.)

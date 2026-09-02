> **FOR INFORMATION ONLY.** Independent, unofficial research — not reviewed, approved, or warranted by anyone. Use at your own risk.

# ADR-004: Agent identity provisioning and credential lifecycle pattern

**Status:** Draft
**Date:** 2026-09-02
**Traces to:** ASR-005, ASR-008

## Context
ASR-005 requires every agent to hold its own scoped identity rather than inheriting one; ASR-008 requires every credential issued to an agent to be time-bounded and independently revocable. Neither is enforceable without a defined provisioning and lifecycle pattern — how an agent's identity is issued, what form its credential takes, how it expires, and how it can be revoked without touching whatever issued it.

## Decision
| Stage | Pattern |
|---|---|
| Issuance | Each agent is provisioned its own cryptographically distinct identity credential at deployment — never a shared service-account key or a credential borrowed from an invoking user — following an identity-federation model such as SPIFFE/DID rather than a static API key. |
| Scope binding | The credential encodes the agent's entitlement scope at issuance; scope is not separately inferred at request time from whatever system happens to authenticate the request. |
| Expiration | Every credential carries a bounded time-to-live; there is no standing, non-expiring agent credential. |
| Revocation | Revocation is available as an operation independent of the system that performed issuance — revoking one agent's credential must not require disabling the identity-provisioning system itself. |
| Rotation | Credential rotation follows a defined schedule shorter than the credential's own maximum lifetime, so expiration is a routine event, not an incident-response action. |

## Corpus reference
An open-source agent-governance toolkit implements this pattern as working reference infrastructure — SPIFFE/DID/mTLS-based per-agent identity, backed by a formally specified, 135-test conformance suite (AgentMesh Identity and Trust) covering credentials, trust scoring, and delegation chains (Microsoft Agent Governance Toolkit; github.com/microsoft/agent-governance-toolkit). Cited as precedent that this pattern is buildable and already implemented as open-source infrastructure, not as authority for adopting it as-is.

## Consequences
- Establishes the mechanism ASR-005 and ASR-008 both depend on; a future capability-specific ADR should assume this pattern is in place rather than re-derive an identity model.
- Does not itself select a specific identity-federation technology (SPIFFE, DID, or otherwise) for adoption — that remains an implementation decision outside this ADR's scope.
- Does not itself define the credential's specific maximum lifetime or rotation interval — left as a case-by-case parameter.

## Amendment log
- 2026-09-02 — Initial version.

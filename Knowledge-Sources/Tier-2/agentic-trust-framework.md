# Agentic Trust Framework (ATF)

**Tier:** 2 — Credible research or production evidence; cite as evidence, not as a standard
**Catalog link:** github.com/massivescale-ai/agentic-trust-framework
**Date pulled:** 2026-09-02
**Repo stats at pull time:** 74 stars · 13 forks · 13 open issues · created 2025-08-06 · last pushed 2026-04-11 · Spec license: CC BY 4.0 · Repo license: Apache 2.0
**Spec version:** v0.9.1, Public Review Draft, April 2026

## Catalog caveat (carried forward from Knowledge-Source-References.md)

> Single-author work (Josh Woodruff, MassiveScale.AI), CSA-amplified via blog/RSAC coverage but **not a CSA-authored standard** — cite as industry practice, not as a CSA specification.

## What it contributes

Zero Trust (NIST 800-207 lineage) applied to AI agents; maturity levels mapped 1:1 to the AWS Scoping Matrix (Scopes 1–4).

## Overview (from README)

An open governance specification for autonomous AI agents, applying Zero Trust principles across five core security elements. Published through the Cloud Security Alliance blog and licensed CC BY 4.0. **This is a specification, not a code library** — implementations demonstrate it in practice; the repo itself doesn't ship a reference implementation.

## The five core elements

| # | Element | Question | What it governs |
|---|---|---|---|
| 1 | Identity | "Who are you?" | Agent credentials, authentication, ownership |
| 2 | Behavior | "What are you doing?" | Monitoring, anomaly detection, intent alignment |
| 3 | Data Governance | "What are you eating? What are you serving?" | Input validation, PII protection, output filtering |
| 4 | Segmentation | "Where can you go?" | Access boundaries, least privilege, blast radius |
| 5 | Incident Response | "What if you go rogue?" | Kill switches, circuit breakers, containment |

## Agent maturity model

Agents earn autonomy through demonstrated trustworthiness — not by default — and can be **demoted** at any time; a critical incident triggers immediate demotion to Intern.

| Level | Name | Autonomy | Human involvement | AWS Scope |
|---|---|---|---|---|
| 1 | Intern | Observe + Report | Continuous oversight | Scope 1 |
| 2 | Junior | Recommend + Approve | Human approves all actions | Scope 2 |
| 3 | Senior | Act + Notify | Post-action notification | Scope 3 |
| 4 | Principal | Autonomous | Strategic oversight only | Scope 4 |

Full promotion gates, demotion criteria, operating model, and deployment checklists are in the repo's `MATURITY_MODEL.md` (not mirrored here — see repository for the current text).

## Ecosystem adoption claimed in README

| Project | Organization | Relationship | ATF coverage |
|---|---|---|---|
| Agent Governance Toolkit | Microsoft | Independent convergence | All 5 elements |
| VERA | Berlin AI Labs | Built on ATF principles | All 5 elements + maturity model |

*(Independent verification of these claimed relationships has not been performed — noted per this catalog's Tier 2 standard of "cite as evidence, not as a standard.")*

## Framework relationships (as ATF's own README positions it)

| Framework | Relationship | One-liner |
|---|---|---|
| CSA AICM | Parent umbrella | AICM defines 243 controls for AI broadly; ATF operationalizes the agent-specific subset |
| MAESTRO | Complementary | MAESTRO identifies what could go wrong; ATF defines how to maintain control |
| OWASP Agentic Top 10 | Complementary | OWASP tells you the threats; ATF provides governance to mitigate them |
| NIST 800-207 | Foundational | NIST provides Zero Trust principles; ATF applies them to AI agents |
| AWS Scoping Matrix | Directly aligned | ATF maturity levels map 1:1 to AWS Scopes 1–4 |
| ISO/IEC 42001 | Directly aligned | ISO 42001 asks if you have an AI management system; ATF helps build the agent-governance component |

## Specification documents (in repo, not mirrored here)

`SPECIFICATION.md` (RFC 2119 requirements) · `MATURITY_MODEL.md` · `CONFORMANCE.md` (conformance tiers, 25 core requirements) · `IMPLEMENTATION_PATTERNS.md` · `CROSSWALKS.md` (AICM/OWASP/NIST/ISO mappings) · `SECURITY.md`

## Background / provenance

Builds on *Agentic AI + Zero Trust: A Guide for Business Leaders* (Sept. 2025), foreword by John Kindervag (creator of Zero Trust). Published on the Cloud Security Alliance blog Feb. 2026 via a joint Zero Trust Working Group / AI Safety Working Group collaboration — this CSA blog publication is the basis of the "CSA-amplified" characterization in this library's catalog; it is not the same as CSA authoring or ratifying the spec itself.

- **Author:** Josh Woodruff, MassiveScale.AI
- **Spec site:** agentictrustframework.ai
- **Self-assessment tool:** verifiedagents.ai/assess

## License

Specification: CC BY 4.0. Repository code/docs: Apache License 2.0.

---
*Extracted via direct read of the repository's README and GitHub API metadata (github.com/massivescale-ai/agentic-trust-framework, `main` branch). Linked spec documents (SPECIFICATION.md, MATURITY_MODEL.md, etc.) were not individually pulled — this note summarizes only the top-level README.*

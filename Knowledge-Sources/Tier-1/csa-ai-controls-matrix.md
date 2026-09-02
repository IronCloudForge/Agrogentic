# CSA AI Controls Matrix (AICM)

**Tier:** 1 — Institutional or vendor-backed; citable in official work
**Catalog link:** cloudsecurityalliance.org (AICM)
**Primary artifact page:** cloudsecurityalliance.org/artifacts/ai-controls-matrix-v1-1
**Date pulled:** 2026-09-02

## What it contributes to this library

243 vendor-agnostic control objectives across 18 domains, mapped to ISO/IEC 42001, NIST AI RMF, SOC 2. Cloud Security Alliance's own institutional work product, built on their established Cloud Controls Matrix lineage.

## What it is

"A first-of-its-kind vendor-agnostic framework for cloud-based AI systems," helping organizations develop, implement, and operate AI technologies securely and responsibly, across organizational, technical, and societal dimensions.

## Origin and lineage

Builds directly on CSA's Cloud Controls Matrix (CCM) — "stands on the robust foundation of our widely-adopted Cloud Control Matrix, leveraging years of expertise in cloud security to address the unique challenges of AI systems." Primary author credited: Daniele Catteddu, CSA Chief Technology Officer.

## Version history (as observed across two CSA sources pulled)

| Source | Date | Domains | Control objectives |
|---|---|---|---|
| CSA blog announcement | July 10, 2025 | 18 | 243 |
| CSA artifact page (v1.1) | June 22, 2026 | 18 | 247 |

*The control-objective count grew from 243 to 247 between the initial announcement and v1.1 — this catalog's "243" figure reflects the original release; note the drift if citing a specific number going forward.*

## The 18 security domains

1. Audit And Assurance
2. Application and Interface Security
3. Business Continuity Management and Operational Resilience
4. Change Control and Configuration Management
5. Cryptography, Encryption and Key Management
6. Datacenter Security
7. Data Security and Privacy Lifecycle Management
8. Governance, Risk and Compliance
9. Human Resources
10. Identity and Access Management (IAM)
11. Interoperability and Portability
12. Infrastructure Security
13. Logging and Monitoring
14. **Model Security** *(AI-specific)*
15. Security Incident Management, E-Discovery & Cloud Forensics
16. **Supply Chain Management, Transparency and Accountability** *(AI-specific)*
17. Threat & Vulnerability Management
18. Universal Endpoint Management

Domains span both traditional security areas (IAM, Data Security) and AI-specific additions (Model Security; Supply Chain Management, Transparency and Accountability).

## Structural pillars (five dimensions each control is organized around)

1. **Control Type** — AI-specific, hybrid AI/cloud, or cloud-specific.
2. **Control Applicability & Ownership** — responsibility mapping across the service stack.
3. **Architectural Relevance** — coverage from the physical layer through the data layer.
4. **Lifecycle Relevance** — coverage from preparation through service retirement.
5. **Threat Category** — nine critical threat classifications (specific names not enumerated in sources pulled).

## Standards mappings

ISO/IEC 42001:2023 · ISO 27001 · BSI AIC4 Catalogue (German/European) · NIST AI RMF & NIST AI 600-1 · EU AI Act. *(Per the July 2025 announcement, the ISO 42001 and EU AI Act mappings were scheduled for an August 2025 follow-on release — confirm current mapping completeness against the live artifact page if citing specifics.)*

## Complementary components

- **CAIQ for AI (AI-CAIQ)** — Consensus Assessment Initiative Questionnaire for AI: self-evaluation and vendor-assessment questionnaire.
- **Implementation Guidelines** and **Auditing Guidelines** — tailored to five organizational roles: Model Provider, Orchestrated Service Provider, Application Provider, AI Customer, Cloud Service Provider.
- Freely downloadable: control matrix spreadsheet, AI-CAIQ, guidelines, and supporting resources.

## Ecosystem integration

Functions as the technical foundation for CSA's broader trustworthy-AI ecosystem: the **AI Trustworthy Pledge** (voluntary commitment to responsible AI practices) and the **STAR for AI Program** (certification pathway, formal launch targeted for late 2025 per the original announcement).

---
*Extracted via automated fetch of the CSA artifact page (v1.1) and the original July 2025 CSA blog announcement, cross-checked against a third-party domain-list summary (resilientcyber.io) for the enumerated 18 domains, since neither primary CSA page fetched provided the full domain list as plain text. cloudsecurityalliance.org's own site was not directly reachable via curl from this environment; all fetches used the WebFetch tool.*

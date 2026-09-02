# Eticas AI Risk Taxonomy

**Tier:** 2 — Credible research or production evidence; cite as evidence, not as a standard
**Catalog link:** arxiv.org/pdf/2607.02201
**Date pulled:** 2026-09-02
**Note:** The arXiv PDF was not directly downloadable from this environment (blocked at the network layer); no local copy of the PDF is archived here. Content below was extracted from the arXiv HTML render (arxiv.org/html/2607.02201v1), which contains the full paper text.

## What it contributes to this library

Documents that every *binding* compliance framework (EU AI Act, etc.) predates agentic AI as a deployment paradigm; only purpose-built frameworks from 2025+ provide direct agentic coverage. Useful for framing governance urgency in general, standards-agnostic terms.

## Bibliographic

- **Title:** The Eticas AI Risk Taxonomy: Open Infrastructure for Operationalizing AI Audits
- **Authors:** Gemma Galdon Clavell, Pablo Accuosto, Usman Gohar (Eticas.ai)
- **Publication:** arXiv:2607.02201v1 [cs.CY], July 2026
- **Citation:** Eticas. (2026). Eticas AI Risk Taxonomy, v2.0.0. https://taxonomy.eticas.ai/risk/
- **License:** CC BY 4.0 (conceptual layer only; proprietary methodology layer retained by Eticas)

## Abstract summary

74+ AI risk taxonomies exist, but almost none show how to convert abstract risk concepts into executed audits with measured grades. Eticas taxonomy v2.0.0 bridges this with an operationalization methodology validated against real systems: 76 active subcategories across 10 categories, mapped to 18 external frameworks, published as open semantic infrastructure under CC BY 4.0.

## Core argument — the agentic AI governance gap (Section 5.4 / Table 5)

**Every binding compliance framework predates agentic AI deployment as a paradigm.**

| Period | Frameworks |
|---|---|
| Pre-2024 (binding) | EU AI Act (2024), ISO/IEC 42001:2023, NIST AI RMF (2023), NIST AI 600-1 (2024), OECD Principles, Council of Europe Convention |
| 2025–2026 (purpose-built for agentic AI) | AIUC-1, CSA Agentic Profile, OWASP Top 10 for Agentic Applications, IBM AI Risk Atlas (updated) |

The authors call this a "structural gap, not an incidental one": regulatory frameworks run on multi-year development cycles, while agentic AI emerged as a deployment paradigm in roughly eighteen months.

**Purpose-built agentic frameworks (only four identified):**
1. **AIUC-1 (2025)** — "SOC 2 for AI agents," six control domains, independent auditing; aligned to EU AI Act, NIST AI RMF, ISO 42001.
2. **CSA Agentic Profile (2025)** — extends NIST AI RMF 1.0; autonomy-tier classification, tool-use risk, runtime behavior governance.
3. **OWASP Top 10 for Agentic Applications (Dec. 2025)** — community-developed, ten agent-specific categories (goal hijacking, tool misuse, cascading failures).
4. **IBM AI Risk Atlas (2025+)** — dedicated agentic category alongside lifecycle-stage organization.

## Taxonomy structure — three-level hierarchy

10 categories (8 established, 2 emerging) → 20 sub-groups (17 established, 3 emerging) → 76 active subcategories (33 established, 43 emerging). Reflects operational audit experience across 50+ systems in twelve sectors, not theoretical optimization.

**Eight established categories:** Bias and Fairness; Privacy and Confidentiality; Reliability; Governance; Security and Misuse; Environmental Impact; Transparency and Explainability; **Agentic AI** (autonomous actions/tool use, multi-agent integrity — emergent behavior, coordination failure).

**Two emerging categories:** Autonomy and Agency (overreliance, automation bias, loss of meaningful control); Organisational Readiness.

## Operationalization layer — four-layer architecture

| Layer | Content | Reusability |
|---|---|---|
| 1: Foundations | Audit process, taxonomy, grading rules, reporting format | Across all audits |
| 2: Technology-Specific | Test approaches, metrics, severity thresholds per system class (LLM, ADM) | Per system type |
| 3: Sector Annexes | Domain-specific adjustments | Per sector |
| 4: Project Instantiation | Specific audit of a specific system, measured data | Engagement-only |

**Worked example (Section 2.1) — PII leakage against GPT-4-0314** using DecodingTrust Privacy Scenario 2: zero-shot baseline 0% disclosure (Severity 1) → single in-context demonstration 51% (Severity 4) → three reinforced demonstrations 84% (Severity 5). Subcategory grade E with SYSTEMIC pattern flag.

**Measurement-to-grade chain:** Probe → Check → Metric Value → Severity (0–5) → Subcategory Grade (A–E) → Dimension Grade (A–E, breadth-adjusted).

**Ontological separation (risks vs. mechanisms vs. causes):** Risk = abstract harm (e.g. "members of protected group receive worse outcomes"); Mechanisms = concrete surfaces where risk emerges (e.g. intersectional unfairness, accessibility barriers); Causes/Interventions = root-cause/remedial level (e.g. unrepresentative training data). The mechanisms field is the published "contract surface" other methodologies can attach test designs to and remain comparable.

## Framework alignment — three-tier mapping (18 frameworks)

- **Compliance tier (6):** EU AI Act, ISO/IEC 42001:2023, AIUC-1, Council of Europe Convention, IEEE 7001/7002/7003.
- **Reference tier (7):** NIST AI RMF, NIST AI 600-1, OECD Principles, TC260, CSA Agentic Profile, OWASP, IEEE 2894.
- **Academic/vocabulary tier (5):** MIT V4, AIR 2024, IBM Atlas, W3C DPV.

Strongest cross-framework consensus: Bias and Fairness, Privacy and Confidentiality, Security and Misuse. Narrowest: Environmental Impact. **Purpose-built only: Agentic AI** — only CSA Agentic Profile, OWASP, AIUC-1, and IBM Atlas provide close matches; every other mapped framework predates agentic emergence.

**NIST AI 600-1 completeness check (Table 4):** of NIST's 12 discrete generative-AI risk categories — 7 directly covered, 4 partially covered, 1 true gap (intellectual property; captured only as an emerging "confidential-information-leakage" subcategory, copyright/patent questions remain out of audit scope). The paper explicitly prefers "named gaps over weak matches."

## Validation

Methodology operationalized across Bias, Fairness, Privacy, Confidentiality, Reliability, Security, Misuse, Governance dimensions; validated against the public DecodingTrust benchmark (Privacy and Bias dimensions). Open infrastructure: stable per-concept URIs (`taxonomy.eticas.ai/risk/[concept-id]`), machine-readable SKOS/Turtle and JSON-LD distributions.

## Positioning against related work

- **MIT AI Risk Repository V4:** comprehensive (300+ sources, 74 frameworks) but no operationalization; normalizes heterogeneous vocabularies.
- **AIR 2024:** 314 types extracted from regulations, includes AIR-Bench, but targets model-safety benchmarking rather than system-context audits.
- **IBM AI Risk Atlas:** lifecycle-stage organized, includes an agentic category, emphasizes automated detection.
- **NIST AI RMF:** process-oriented (Govern/Map/Measure/Manage functions) — describes organizational activities, not measured system properties.
- **NIST AI 600-1:** 12 bounded generative-AI risk areas, audit-relevant but incomplete for agentic systems.
- **W3C DPV:** the semantic-infrastructure pattern (SKOS + stable URIs) Eticas explicitly adopts.

## Key findings / conclusions

1. Operationalization is achievable and demonstrated end-to-end (Section 2 worked example).
2. A risks-vs-mechanisms ontology enables interoperability across different audit methodologies.
3. Audit-oriented granularity (10/20/76) connects regulation to testable criteria without overwhelming audit teams.
4. **Agentic AI exposes a structural governance lag** — binding frameworks predate agentic emergence by 1–3 years; purpose-built frameworks only emerged 2025–2026.

**Concluding statement:** "Infrastructure matters as much as method" at this stage of AI-audit maturity — individual skilled audits succeed ad hoc, but the field cannot accumulate learning, regulators cannot evaluate consistency, and clients cannot compare services without shared, open, operationalizable foundations. Eticas publishes the taxonomy as an open, extensible scaffold rather than a claimed sole-correct organization.

## Access

- Public taxonomy: `https://taxonomy.eticas.ai/`
- Machine-readable distributions: `/dist/taxonomy.ttl`, `/dist/taxonomy.jsonld`

---
*Extracted via automated fetch of the arXiv HTML full-text render (arxiv.org/html/2607.02201v1); the PDF itself could not be downloaded directly in this environment.*

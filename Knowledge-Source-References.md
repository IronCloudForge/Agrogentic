# Knowledge Source References — Layer 3 Corpus

This is the standing catalog of external, independently reproducible Layer 3 sources referenced or vetted for this library (see `Layer-Model.md`). Every `Corpus evidence` / `Corpus reference` citation in an ASR or ADR should trace back to an entry here. This catalog is evidentiary, never authoritative — it corroborates that a requirement is real and shows how others have addressed it; it does not obligate the architecture to anything on its own.

Sources are organized by credibility tier. Tier assignment reflects institutional backing, transparency of authorship, and reproducibility — not agreement with any particular position.

## How to add a source

1. Verify authorship/institutional backing before adding — check who maintains it, not just what it claims.
2. Assign a tier honestly. A source doesn't need to be Tier 1 to be useful; it needs its tier stated accurately so a reader can weigh it correctly.
3. Link directly to the primary source (the repository, the paper, the standards page) — not to a secondary write-up about it.
4. Note the date pulled and, where it matters, the date of the underlying data (a repo's stars/commit count or a benchmark's results are point-in-time facts).

---

## Tier 1 — Institutional or vendor-backed; citable in official work

| Source | Link | What it contributes |
|---|---|---|
| OWASP Agentic Skills Top 10 (AST10) | github.com/OWASP/www-project-agentic-skills-top-10 | Skill/behavior-layer threat taxonomy (AST01–AST10); incident timeline (ClawHavoc, ToxicSkills, ClawJacked); the "lethal trifecta" risk heuristic; Universal Skill Format proposal. OWASP Incubator project, CC-BY-SA 4.0, led by Ken Huang (OWASP AIVSS Lead). |
| OWASP Top 10 for Agentic Applications (2026) | genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026 | Model/reasoning-layer agentic risk taxonomy; the sibling project AST10 extends downward into the skill layer. |
| Microsoft Agent Governance Toolkit (AGT) | github.com/microsoft/agent-governance-toolkit | Working, MIT-licensed reference implementation of deterministic policy enforcement, per-agent identity (SPIFFE/DID), execution sandboxing (privilege rings), and kill-switch/SRE controls. Public preview; 29 architecture decision records; 992 conformance tests against 10 formal specs. |
| MITRE SAFE-AI | atlas.mitre.org/pdf-files/SAFEAI_Full_Report.pdf | Maps AI/ATLAS threat techniques directly onto ~100 NIST SP 800-53 Rev 5 controls; includes assessor interview Q&A sets for planning Security Control Assessments. MITRE (FFRDC) work product, not a vendor. |
| MITRE ATLAS | atlas.mitre.org | Adversarial threat-tactic/technique knowledge base for AI systems; the taxonomy SAFE-AI maps onto. Ongoing "Secure AI" partnership with the Center for Threat-Informed Defense for incident sharing. |
| CSA AI Controls Matrix (AICM) | cloudsecurityalliance.org (AICM) | 243 vendor-agnostic control objectives across 18 domains, mapped to ISO/IEC 42001, NIST AI RMF, SOC 2. Cloud Security Alliance's own institutional work product, built on their established Cloud Controls Matrix lineage. |
| IBM AI Atlas Nexus | github.com/IBM/ai-atlas-nexus | Ontology/knowledge graph unifying IBM's AI Risk Atlas, MIT AI Risk Repository, NIST GenAI Profile, and OWASP's LLM/Agentic Top 10s. Useful for cross-walking vocabulary across frameworks rather than as a control set of its own. |

## Tier 2 — Credible research or production evidence; cite as evidence, not as a standard

| Source | Link | What it contributes |
|---|---|---|
| Uber ADR (paper) | arxiv.org/abs/2605.17380 | Production-deployed (10 months, 7,200+ hosts, 200,000+ sessions/day at 2026 scale) enterprise agentic detection system. Accepted MLSys 2026 Industry Track. Empirical detection rates by threat tactic, ablation studies on verification-context value, credential-exposure findings. |
| Uber ADR (code + ADR-Bench) | github.com/uber/ADR | Open-source Sensor, Detector, and ADR-Bench (302 tasks, 133 MCP servers, 17 techniques across 5 tactics) — the most MCP-native, broadly-covering agentic security benchmark identified to date. |
| Uber ADR (MLSys slides) | mlsys.org/media/mlsys-2026/Slides/3853_k9cXWDE.pdf | Franker, talk-format deployment findings not in the paper: human-accountability breakdown ("YOLO mode," approval fatigue), corrected misconceptions (prompt injection overweighted, supply-chain attacks underweighted), and open/unresolved problems (excessive vs. insufficient agency, hallucination as scope creep). |
| Eticas AI Risk Taxonomy | arxiv.org/pdf/2607.02201 | Documents that every *binding* compliance framework (EU AI Act, etc.) predates agentic AI as a deployment paradigm; only purpose-built frameworks from 2025+ provide direct agentic coverage. Useful for framing governance urgency in general, standards-agnostic terms. |
| Agentic Trust Framework (ATF) | github.com/massivescale-ai/agentic-trust-framework | Zero Trust (NIST 800-207 lineage) applied to AI agents; maturity levels mapped 1:1 to the AWS Scoping Matrix (Scopes 1–4). **Caveat:** single-author work (Josh Woodruff, MassiveScale.AI), CSA-amplified via blog/RSAC coverage but not a CSA-authored standard — cite as industry practice, not as a CSA specification. v0.9.1, Public Review Draft as of April 2026. |

## Tier 3 — Unverified or low institutional confidence; do not cite without independent verification

| Source | Note |
|---|---|
| "AI SAFE²" framework (CyberStrategyInstitute) | Marketing-heavy self-description ("the race is over, we built the bridge"), no visible institutional authorship identified. Not verified; not cited anywhere in this library. |
| Generic GitHub `grc` topic repositories | 230+ repositories of wildly uneven quality and provenance; treat each individually if ever needed — do not cite the topic or category as a source. |
| Secure Agentic Framework (SAF) | secureagenticframework.org — well-built on inspection (85 techniques, 14 MITRE-ATT&CK-aligned tactics, large crosswalk to EU AI Act/NIST 800-53/AI RMF/SSDF), but institutional backing/authorship has not yet been independently verified. Do not cite until verified. |

---

## Amendment log
- 2026-08-31 — Initial catalog, compiling sources identified during the research session preceding this library's four-layer alignment update.

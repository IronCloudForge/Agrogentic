# Documentation Architecture — Four-Layer Model

This document is the canonical reference for how the Agentic AI governance documentation library is structured. Every other document in this library (ASR template, ADR template, individual ASRs/ADRs, the Logs, the Outline Catalog, and the Research-to-Governance Crosswalk) should point to this file rather than re-explaining the model inline.

## The four layers

**Layer 1 — Authority.** The signed instrument: whatever the AI CIO, or the authorizing OCIO SES, formally signs. This is the only layer with actual authorizing weight, analogous to an ATO memo. It is not a parallel summary of the layers below it — it is a **compiled, authorized snapshot** of Layer 2 at a specific point in time, and should cite the specific version or state of the ASR/ADR Log it represents.

**Layer 2 — Architecture requirements and decisions.** The ASR Log, the ADR Log, and the individual ASR/ADR documents themselves, plus any solution and technical detail that implements them. This is the working layer: where requirements get stated, decisions get made, and both remain independently traceable. Layer 2 is constrained by Layer 4 and corroborated by Layer 3. Once mature and accepted, it is what Layer 1 compiles and authorizes.

**Layer 3 — Knowledge sources.** The external industry corpus: published research, production case studies, and open-source reference implementations — e.g., OWASP Agentic Skills Top 10, MITRE SAFE-AI, Uber's ADR system and ADR-Bench, Microsoft's Agent Governance Toolkit, CSA's AICM and Agentic Trust Framework. This layer is **evidentiary, not authoritative**. It corroborates that a requirement is real, shows how others have solved a comparable problem, and gives a requirement independently reproducible grounding — but it never obligates USDA to do anything on its own. Every Layer 3 citation should link directly to its source (a GitHub repository, a paper, a standards-body publication) so a reader can verify it independently. The standing, tiered catalog of vetted Layer 3 sources is maintained in `Knowledge-Source-References.md` — every `Corpus evidence` citation in an ASR should trace back to an entry there.

**Layer 4 — Federal Standards.** All of it — not only AI-specific material. NIST SP 800-53 Rev 5, SP 800-207 (Zero Trust), SP 800-128 (configuration management), SP 800-137 (continuous monitoring), FIPS 199, FedRAMP and the OSCAL mandate, OMB memoranda, CISA ZTMM, relevant Executive Orders, alongside NIST AI RMF and any AI-specific overlays. This is the layer that actually obligates the architecture to do something. AI-specific standards are additive to this layer, not a replacement for the cloud and on-prem baseline that already governs it.

## Directionality

- **Layer 4 constrains Layer 2.** Every ASR's `Driver` field cites here. This is the requirement's authority.
- **Layer 3 corroborates Layer 2.** Every ASR's `Corpus evidence` section cites here. This is proof the requirement is real and solvable, never the source of the obligation itself.
- **Layer 2 compiles into Layer 1.** Once a set of ASRs/ADRs is accepted and stable, it becomes the basis for what gets formally authorized.

## Driver field family tags

Every ASR's `Driver` field must carry one or more family tags identifying which part of Layer 4 it draws on. This keeps a bare citation from leaving ambiguous whether a requirement rests on AI-specific policy, cloud-specific standards, on-prem-specific standards, or a control that applies regardless of deployment substrate.

| Tag | Scope |
|---|---|
| **[AI]** | Standards, policy, or executive direction specific to artificial intelligence systems — e.g., NIST AI RMF, OMB M-25-21, EO 14179, EO 14110, and any AI-specific control overlays. |
| **[CLOUD]** | Standards specific to cloud-hosted or cloud-native systems — e.g., FedRAMP, the OSCAL mandate. |
| **[ON-PREM]** | Standards specific to traditional on-premises infrastructure where the requirement diverges from a cloud-native equivalent. |
| **[CROSS-CUTTING]** | Standards that apply uniformly regardless of deployment substrate — the general NIST SP 800-53 Rev 5 control catalog, Zero Trust architecture (SP 800-207), FIPS 199 categorization, SP 800-128, and SP 800-137 fall here unless a specific control has a cloud- or on-prem-only application. |

An ASR may carry more than one tag if its Driver draws on standards from more than one family (e.g., a requirement governing cloud-hosted AI inference might cite both **[AI]** and **[CLOUD]**).

## Amendment log
- 2026-08-31 — Initial version, establishing the four-layer model and the Driver family-tag convention.

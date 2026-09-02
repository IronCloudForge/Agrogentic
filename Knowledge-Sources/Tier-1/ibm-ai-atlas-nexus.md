# IBM AI Atlas Nexus

**Tier:** 1 — Institutional or vendor-backed; citable in official work
**Catalog link:** github.com/IBM/ai-atlas-nexus
**Date pulled:** 2026-09-02
**Repo stats at pull time:** 139 stars · 40 forks · 19 open issues · created 2024-12-12 · last pushed 2026-08-31 · License: Apache 2.0 · Python ≥3.11, <3.12

## What it contributes to this library

Ontology/knowledge graph unifying IBM's AI Risk Atlas, MIT AI Risk Repository, NIST GenAI Profile, and OWASP's LLM/Agentic Top 10s. Useful for cross-walking vocabulary across frameworks rather than as a control set of its own.

## Overview

Tooling to bring together resources related to governance of foundation models — a community-driven approach to curating and cataloguing datasets, benchmarks, and mitigations, turning abstract risk definitions into actionable workflows. Builds on the IBM AI Risk Atlas, making it a "nexus" of governance assets and tooling. Uses a knowledge graph of an AI system as a unified structure linking and contextualizing heterogeneous domain data. Stated intent: create a starting point for an open AI Systems ontology, focused on risk, that the community can extend.

## Features

- An ontology combining the AI-risk view (taxonomies, risks, actions) with an AI-model view (AI systems, AI models, model evaluations) into one coherent schema.
- AI risks collected from: **IBM AI Risk Atlas, IBM Granite Guardian, MIT AI Risk Repository, NIST AI RMF Generative AI Profile, AI Risk Taxonomy (AIR 2024), AILuminate Benchmark, Credo's Unified Control Framework, OWASP Top 10 for LLM Applications, OWASP Top 10 for Agentic Applications, and OWASP Agentic Skills Top 10.**
- Proposed mappings between taxonomies, and between risks and actions.
- Python library methods to explore available risks, relations, and actions, and to detect potential risks in a given use case.
- Downloadable exported graph populated with data instances.
- Example use case: auto-assistance in compliance questionnaires using Chain-of-Thought examples.
- Tooling to convert the LinkML schema and instance data into a Cypher representation for populating a graph database.

## Notable cross-references this library should know about

This is the **only Tier 1 source that explicitly ingests and cross-maps all three of**: OWASP Top 10 for LLM Applications, OWASP Top 10 for Agentic Applications, **and** OWASP Agentic Skills Top 10 — the same three taxonomies this catalog treats as separate Tier 1 entries (model layer, skill layer). AI Atlas Nexus is the crosswalk between them, not a fourth independent taxonomy.

## Resources / notebooks (in repo, not individually pulled)

- LinkML schema documentation (`docs/ontology/index.md`) and instance data for an example knowledge graph.
- Notebooks: Quickstart, Risk identification, Auto-assist questionnaire, AI Tasks identification, AI Domain identification, Risk Categorization (prompt templates credited to arXiv:2407.12454), Crosswalk generation, Risk-to-ARES Evaluation (robustness evaluation integration).
- Related: `ai-atlas-nexus-demos` and `ai-atlas-nexus-extensions` companion repos; IBM AI Risk Atlas; "Usage Governance Advisor: From Intent to AI Governance" (arXiv:2412.01957).

## Installation (as documented)

```bash
pip install "ai-atlas-nexus[INFERENCE_LIB]"   # INFERENCE_LIB in {ollama, vllm, wml, rits}
```

Requires an LLM inference backend to infer risks/risk data — supports IBM Watsonx AI (WML), Ollama, vLLM, and RITS (IBM-internal only).

## License

Apache 2.0.

---
*Extracted via direct read of the repository's README and GitHub API metadata (github.com/IBM/ai-atlas-nexus, `main` branch). The LinkML ontology schema, notebooks, and knowledge-graph export were not individually pulled — only the README's own description of them.*

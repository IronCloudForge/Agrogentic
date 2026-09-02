# Uber ADR (code + ADR-Bench)

**Tier:** 2 — Credible research or production evidence; cite as evidence, not as a standard
**Catalog link:** github.com/uber/ADR
**Date pulled:** 2026-09-02
**Repo stats at pull time:** 1,523 stars · 139 forks · 16 open issues · created 2026-04-19 · last pushed 2026-09-01 · License: Apache 2.0 (with `Detection/benchmark/agentdojo/` vendored under its own MIT license)

## What it contributes to this library

Open-source Sensor, Detector, and ADR-Bench (302 tasks, 133 MCP servers, 17 techniques across 5 tactics) — the most MCP-native, broadly covering agentic security benchmark identified to date. Companion repository to [`uber-adr-paper-mlsys2026.md`](./uber-adr-paper-mlsys2026.md).

## Repository description (from GitHub)

> ADR secures enterprise AI agents through observability, security benchmarking, and threat detection. Deployed at Uber.

## What's open-sourced vs. not

This repo contains the open-source **ADR Discovery**, **ADR Sensor**, **ADR-Bench**, and **ADR Detector** described in the paper. Two components from the paper are explicitly *not* included:
- **ADR Explorer** (the offline red-teaming engine that hardens detection via pre-deployment adversarial discovery) — withheld.
- **ADR Prevention** (stopping unsafe actions before they cause harm) — "not included in the current open-source release. Stay tuned."

## Five capabilities described in the README

1. **ADR Discovery** — inventories installed AI apps, CLI agents, IDE extensions, local model runtimes, and MCP servers on an endpoint; flags unknown surfaces for review.
2. **ADR Observability (Sensor)** — captures agent intent, tool use, and execution traces across 7+ AI coding tools on macOS, Linux, and Windows, plus internal automation and customer-facing support agents.
3. **ADR Benchmark** — ADR-Bench: 300+ tasks, 133 MCP servers, all 17 agent attack techniques.
4. **ADR Detection** — two-tier architecture (high-recall triage + deeper agentic reasoning for suspicious sessions).
5. **ADR Prevention** — not included in this release.

## Repository layout

| Path | ADR component | Description |
|---|---|---|
| `Discovery/` | ADR Discovery | Inventory of AI apps, CLI agents, IDE extensions, model runtimes, MCP servers on an endpoint |
| `Sensor/` | ADR Observability | Telemetry collection/normalization from Claude Code, Cursor, Codex, opencode, Claude Desktop, and others |
| `Detection/` | ADR Benchmark + Detection | Dual-agent detector, 133 MCP servers, 303 benchmark tasks, baselines, figure scripts |
| `docs/REPRODUCIBILITY.md` | Evaluation | Step-by-step workflow to reproduce benchmark detection and paper figures |
| `docs/adr-paper.pdf` | — | The accepted MLSys 2026 paper — see [`uber-adr-paper-mlsys2026.md`](./uber-adr-paper-mlsys2026.md) |
| `docs/adr-mlsys-2026-slides.pdf` | — | The MLSys 2026 talk slides — see [`uber-adr-mlsys2026-slides.md`](./uber-adr-mlsys2026-slides.md) |

## Quick start (from README)

```bash
git clone https://github.com/uber/ADR
cd ADR/Detection
uv sync
export ANTHROPIC_API_KEY="..." OPENAI_API_KEY="..."
```

Default detector is `adr` (ADR dual-agent). Keyless smoke tests available via `--detector llamafirewall`.

## Data notice

`Detection/` includes **synthetic** benchmark fixtures (fake credentials, emulated environments, prompt-injection scenarios) for defensive security research only, per `docs/OPEN_SOURCE_REVIEW.md`.

## Citation

```bibtex
@inproceedings{li2026adr,
  title={ADR: An Agentic Detection System for Enterprise Agentic AI Security},
  author={Li, Chenning and Hu, Pan and Xu, Justin and Ozbas, Baris and Liu, Olivia and Van, Caroline and Li, Manxue and Zhou, Wei and Alizadeh, Mohammad and Zhang, Pengyu and Sriramadhesikan, KK and Zhang, Ming},
  booktitle={Proceedings of the Ninth Conference on Machine Learning and Systems},
  year={2026}
}
```

---
*Extracted via direct read of the repository's README and GitHub API metadata (github.com/uber/ADR, `main` branch). Not cloned in full — the paper and slides PDFs the README links to were downloaded separately as the two files above.*

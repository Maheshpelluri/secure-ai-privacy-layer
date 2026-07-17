# Secure AI Privacy Layer

[![Architecture Phase](https://img.shields.io/badge/status-architecture%20phase-1f7a8c?style=flat-square)](docs/implementation-roadmap.md)
[![Research Project](https://img.shields.io/badge/type-research%20project-6b4f00?style=flat-square)](docs/future-research.md)
[![License: MIT](https://img.shields.io/badge/license-MIT-2b7a0b?style=flat-square)](LICENSE)
[![Documentation](https://img.shields.io/badge/docs-complete-0f4c81?style=flat-square)](docs/architecture.md)
[![GitHub Stars](https://img.shields.io/badge/github-stars-lightgrey?style=flat-square)](README.md)
[![Last Commit](https://img.shields.io/badge/last-commit-lightgrey?style=flat-square)](README.md)

**An architectural research initiative exploring a provider-independent privacy layer for Public AI workflows.**

> **Status: Architecture & Research Phase.** This repository currently contains a conceptual architecture, design rationale, and open research questions. It does not yet contain a working implementation. See [`prototype/README.md`](prototype/README.md) for details on why, and what comes next.

---

## Overview

Public AI platforms — ChatGPT, Claude, Gemini, and comparable systems — have become part of everyday knowledge work. As adoption moves from experimentation into operational use, a recurring constraint surfaces across industries: the most useful data to analyze is also, almost by definition, the most sensitive data to expose.

Large enterprises address this today with dedicated AI governance functions, private model deployments, compliance frameworks, and security infrastructure. Most individuals, freelancers, startups, consultants, researchers, and small businesses using the same public AI platforms do not have access to any of this.

This project explores a specific architectural response to that gap: a **provider-independent privacy layer** that sits between a user's data and an AI model, so that sensitive values are withheld from the model itself rather than removed by hand beforehand, and restored automatically once analysis returns.

The full narrative case for this direction — including the problem, current practice, and the concept walked through end to end — is published in [`article/index.html`](article/index.html). **That article is the authoritative source of truth for this project's vision.** This repository exists to give that vision the structure a real engineering effort needs.

## Why This Project Exists

- Public AI adoption is shifting from "can the model do this" to "can we trust this workflow with our real data."
- Existing controls — governance, access control, masking, tokenization, DLP, CASB, private LLM deployments, AI gateways — solve real, adjacent problems, but none of them were built specifically for the moment a user's data meets a public AI model in real time.
- That gap is currently closed manually, by individuals redacting spreadsheets before pasting them into a chat window — a workflow that doesn't scale and isn't audited.
- The intelligence layer of AI is now broadly accessible. The privacy layer around it is not, outside large organizations.

See [`docs/problem-statement.md`](docs/problem-statement.md) and [`docs/market-gap.md`](docs/market-gap.md) for the full discussion.

## What This Is — and Is Not

This project is:
- A conceptual, provider-independent **architecture** for reducing unnecessary exposure of sensitive data to AI models.
- A **research direction**, evaluated openly, including its own limitations and open questions.

This project is **not**:
- Another AI model or chatbot.
- Another AI provider.
- A replacement for enterprise AI platforms, governance frameworks, or compliance tooling.
- A production-ready product, library, or service — see [Current Status](#current-status).

See [`docs/system-boundaries.md`](docs/system-boundaries.md) for the full scope and threat model.

## Architecture Overview

At a conceptual level:

```
Original Data → Privacy Layer → Transformed Dataset → AI Platform
                                                             ↓
Final Output ← Privacy Layer (restores originals) ← Analysis Returned
```

The AI model never receives the original, identifiable values. It reasons over structure and pattern in a transformed dataset; the layer restores original values only when output returns to the user. The full architecture, including trust boundaries, components, and data flow, is described in [`docs/architecture.md`](docs/architecture.md).

Design principles guiding this architecture — provider independence, minimal exposure, analytical fidelity, reversibility, auditability, explainability, workflow compatibility, and extensibility — are detailed in [`docs/design-principles.md`](docs/design-principles.md).

## Repository Structure

```
secure-ai-privacy-layer/
├── README.md
├── LICENSE
├── CHANGELOG.md
├── SECURITY.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
├── CITATION.cff
├── GOVERNANCE.md
├── PROJECT_ROADMAP.md
├── article/
├── docs/
│   ├── community.md
│   ├── releases.md
│   ├── adr/
│   └── rfcs/
├── prototype/
├── examples/
├── assets/
└── .github/
    ├── ISSUE_TEMPLATE/
    ├── workflows/
    ├── PULL_REQUEST_TEMPLATE.md
    ├── FUNDING.yml
    └── labels.md
```

## Current Status

| Area | Status |
|---|---|
| Problem definition & market analysis | Written |
| Architectural concept | Written |
| Design principles | Written |
| System boundaries & threat model | Written |
| Reference implementation | Not started |
| Evaluation results | Not applicable — no implementation yet |
| Provider integrations | Not started |

This project is at the stage of architectural publication, not implementation. Claims in this repository about what the architecture *could* do are proposals, not measured results.

## MVP Scope (Proposed)

A minimal viable exploration — not yet built — would likely need to demonstrate, on a single AI provider and a single structured dataset format:

1. Reliable detection and transformation of a defined set of sensitive field types.
2. Preservation of structure sufficient for an AI model to perform meaningful analysis on the transformed data.
3. Accurate, automatic restoration of original values in the output.
4. A basic audit record of what was transformed and restored.

See [`docs/implementation-roadmap.md`](docs/implementation-roadmap.md) for how this fits into a longer-term phased plan.

## Roadmap

See [`docs/implementation-roadmap.md`](docs/implementation-roadmap.md) for the full phase-by-phase plan, from architecture (Phase 0) through production readiness (Phase 5).

## Vision

If this direction proves out, the intent is for the privacy layer to become one part of a broader, evolving set of workflow components around Public AI — alongside governance, routing, observability, identity, and policy enforcement — available to any user of public AI models, not only organizations with dedicated security infrastructure. See [`docs/future-research.md`](docs/future-research.md) for the open research areas this would depend on.

## Research Disclaimer

This repository describes an architectural direction under active exploration. It intentionally distinguishes between:

- **Established facts** — observable trends in AI adoption and existing practice.
- **Architectural proposals** — the privacy layer concept and its design principles.
- **Research questions** — open problems this architecture has not yet answered.
- **Future work** — capabilities explicitly out of scope for the current direction.

No performance claims, accuracy figures, or production readiness should be inferred from this repository. None currently exist.

## Documentation

| Document | Purpose |
|---|---|
| [`article/index.html`](article/index.html) | The full narrative case — start here for the "why" |
| [`docs/architecture.md`](docs/architecture.md) | Components, data flow, trust boundaries |
| [`docs/problem-statement.md`](docs/problem-statement.md) | The adoption and trust problem in detail |
| [`docs/market-gap.md`](docs/market-gap.md) | Existing approaches and where friction remains |
| [`docs/design-principles.md`](docs/design-principles.md) | The principles guiding this architecture |
| [`docs/system-boundaries.md`](docs/system-boundaries.md) | Scope, threat model, explicit non-goals |
| [`docs/implementation-roadmap.md`](docs/implementation-roadmap.md) | Phased plan from architecture to production |
| [`docs/evaluation-framework.md`](docs/evaluation-framework.md) | How this should eventually be measured |
| [`docs/future-research.md`](docs/future-research.md) | Open research areas: agents, MCP, multimodal, and more |
| [`docs/glossary.md`](docs/glossary.md) | Terminology used throughout this repository |
| [`docs/faq.md`](docs/faq.md) | Direct answers to the most common questions |
| [`docs/limitations.md`](docs/limitations.md) | Known limitations, unknowns, and tradeoffs |

## Contributing

This project is in its research and architecture phase, and contributions of that kind — critique, questions, prior art, adjacent research — are as valuable as code will eventually be. See [`CONTRIBUTING.md`](CONTRIBUTING.md).

## License

Released under the [MIT License](LICENSE).

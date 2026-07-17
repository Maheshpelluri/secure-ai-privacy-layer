# Contributing

Thank you for considering a contribution. This project is in its **architecture and research phase** — there is no implementation yet, and the most valuable contributions right now are conceptual, not code.

## Contribution Philosophy: Research-First

Before this project accumulates code, it needs to accumulate scrutiny. Contributions that challenge, refine, or extend the architecture are treated with the same seriousness as a future pull request against a reference implementation. Specifically, this project values:

- **Critique of the architecture** — gaps, unstated assumptions, or scenarios the design doesn't handle.
- **Prior art** — related work, existing tools, standards, or research this project should be positioned against or learn from.
- **Threat modeling** — ways the boundaries described in [`docs/system-boundaries.md`](docs/system-boundaries.md) could be incomplete.
- **Domain expertise** — sector-specific considerations (healthcare, finance, legal, and others) that the current documents may be missing.
- **Terminology precision** — corrections to [`docs/glossary.md`](docs/glossary.md) or inconsistent usage elsewhere.

Code contributions are welcome once the roadmap reaches an implementation phase (see [`docs/implementation-roadmap.md`](docs/implementation-roadmap.md)), but premature code without architectural consensus is likely to be redirected into discussion first.

## How to Contribute

### 1. Issues

Use GitHub Issues for:
- Architectural questions or gaps.
- Documentation corrections or ambiguities.
- Proposed additions to open research areas.
- Prior art or related work worth referencing.

Please use the issue template in [`.github/ISSUE_TEMPLATE.md`](.github/ISSUE_TEMPLATE.md) and be explicit about whether you're reporting a documentation issue, an architectural concern, or a research question.

### 2. Discussion

For open-ended questions — "has anyone explored X," "how would this interact with Y" — open a Discussion (or an Issue labeled `discussion` if Discussions are not enabled) rather than a Pull Request. Several of the open questions in [`docs/future-research.md`](docs/future-research.md) are explicitly intended to be worked through this way before any implementation is attempted.

### 3. Pull Requests

Documentation pull requests are the primary contribution type at this stage. Please:

- Keep proposals consistent with the existing tone: analytical, evidence-based, and explicit about what is established fact versus proposal versus open question.
- Avoid introducing marketing language, unverified performance claims, or implied production-readiness.
- Reference the relevant `docs/` file(s) your change affects, and update [`CHANGELOG.md`](CHANGELOG.md) under "Unreleased."
- For anything touching the architecture itself, open an Issue first so the change can be discussed before it's written.

Use [`.github/PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md) when submitting.

## What Not to Do

- Don't submit a full implementation without prior architectural discussion — see [`prototype/README.md`](prototype/README.md) for why code doesn't exist yet.
- Don't present speculative capabilities as working features.
- Don't remove the distinctions between established facts, proposals, and open questions when editing documentation.

## Code of Conduct

All contributions are expected to follow [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md).

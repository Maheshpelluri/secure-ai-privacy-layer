# Prototype

## Current status: no code

There is no implementation in this directory yet. This is intentional, not an oversight.

## Why architecture before code

The parts of this project most likely to be wrong — and cheapest to fix while they're still documents — are the problem definition, the scope boundary, and the design principles. Writing a transformation engine before those are stress-tested by outside review risks building a solid implementation of the wrong architecture. The `docs/` directory is where that review is meant to happen first.

## What "Phase 1" will look like when it starts

Per [`../docs/implementation-roadmap.md`](../docs/implementation-roadmap.md), the first prototype is scoped narrowly:

- One data modality: structured tabular data (CSV / spreadsheet-style).
- One transformation strategy: consistent tokenization of a defined set of identifiable field types.
- One AI provider integration, used only to validate the transform → analyze → restore path end to end.
- Offline evaluation against a small, non-sensitive synthetic dataset — not a live or production dataset.

Deliberately out of scope for the first prototype: multimodal input, multi-provider routing, agentic workflows, and anything performance- or scale-related. See [`../docs/future-research.md`](../docs/future-research.md) for why those are harder problems, addressed separately.

## What would need to be true before this directory has real code

- The architecture in [`../docs/architecture.md`](../docs/architecture.md) has had enough outside review that a first implementation isn't just encoding one person's untested assumptions.
- The evaluation approach in [`../docs/evaluation-framework.md`](../docs/evaluation-framework.md) is specific enough to know what "the prototype works" would actually mean.
- Someone is prepared to treat the first version as disposable — likely to be rebuilt once real evaluation data exists, not as a foundation to build on immediately.

## How to help before there's code

- Review the architecture and scope documents in `../docs/` and open issues against specific claims you think are wrong or underspecified.
- If you've built something adjacent (tokenization libraries, PII detection, reversible data transforms), point to prior art in an issue — this project would rather reuse and cite existing work than reinvent it.
- See [`../CONTRIBUTING.md`](../CONTRIBUTING.md) for how discussion and issues are handled at this stage.

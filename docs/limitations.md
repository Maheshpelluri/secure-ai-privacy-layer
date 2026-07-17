# Limitations

This document is meant to be read alongside
[`system-boundaries.md`](./system-boundaries.md), which defines scope. This
document is about honesty regarding what's uncertain or unresolved even _within_
that scope.

## Known limitations

- **No implementation exists.** Every claim in this repository about what the
  architecture could do is a design intention, not a measured outcome. See
  [`../prototype/README.md`](../prototype/README.md).
- **No accuracy figures exist.** Restoration accuracy, transformation latency,
  and analytical fidelity are proposed evaluation dimensions
  ([`evaluation-framework.md`](./evaluation-framework.md)), not results.
- **The transform-and-restore pattern has known hard cases.** Analysis that
  depends on exact values rather than patterns (a specific date triggering a
  specific regulatory threshold, for example) is difficult for a general-purpose
  transformation to handle without either losing the value the analysis needs or
  exposing more than intended.
- **Entity resolution is unsolved here.** Correctly recognizing that two
  differently formatted records refer to the same real-world person or account,
  across a large dataset, is a nontrivial problem independent of this project
  and hasn't been addressed by it.
- **Contextual and temporal relationships that span multiple fields or
  documents** are not well captured by field-level or token-level
  transformation. A privacy layer operating on individual fields may miss
  meaning that only exists across several of them together.
- **Scale is untested.** Nothing in this repository has been evaluated against
  very large, deeply nested, or high-throughput datasets.

## Unknowns

- Whether "consistent, structure-preserving transformation" is achievable across
  arbitrary data types with a single general approach, or whether it requires a
  different strategy per data type.
- How restoration accuracy should be _validated_ on an ongoing basis rather than
  assumed correct after initial testing.
- How this architecture would behave inside multi-step or agentic AI workflows,
  where sensitive data may flow through several tool calls rather than a single
  request-response pair. See [`future-research.md`](./future-research.md).
- Whether provider-side model behavior (e.g., how a model handles unusual
  token-like strings in its input) introduces its own failure modes that a
  transformation layer would need to account for.

## Tradeoffs

- **Minimal exposure vs. analytical fidelity.** The less a model sees, the safer
  the exposure profile — but also the more likely some genuinely useful signal
  is withheld from the analysis. Where this tradeoff should sit is a design
  decision, not a fixed constant, and is likely to be use-case dependent.
- **Provider independence vs. depth of integration.** A layer designed to work
  the same way across providers may not take advantage of provider-specific
  capabilities (e.g., a model's own structured-output or safety features) as
  fully as a provider-specific integration could.
- **Automatic restoration vs. auditability overhead.** Restoring values
  automatically is the point of the architecture, but doing so in a way that's
  independently auditable (see [`design-principles.md`](./design-principles.md))
  adds complexity that a simpler, unaudited restoration step would not require.

## Research assumptions

The current architectural direction assumes:

- That a meaningful fraction of real-world business analysis can be performed
  usefully on structurally-preserved but value-transformed data. This is a
  testable assumption, not yet tested in this project.
- That restoration can be made reliable enough to trust for business use — an
  open question addressed, not answered, in
  [`evaluation-framework.md`](./evaluation-framework.md).
- That provider-independence is a property worth designing for now, rather than
  something to add later. This is a judgment call, discussed in
  [`architecture.md`](./architecture.md), not a proven requirement.

Where any of these assumptions turns out to be wrong, the appropriate response
is to revise the architecture documents, not to quietly work around the
contradiction in an implementation. See [`CONTRIBUTING.md`](../CONTRIBUTING.md).

# Evaluation Framework

This document describes **how** this architecture should eventually be
evaluated. It contains no results, benchmarks, or figures — none exist yet,
because no implementation exists yet (see
[`prototype/README.md`](../prototype/README.md)). Publishing an evaluation
methodology before an implementation is a deliberate choice: it commits the
project to being measured against defined criteria rather than described in
terms that are hard to falsify.

## Dimensions to Evaluate

### Restoration Accuracy

Whether every transformed value in the AI's output is correctly and completely
restored to its original form, with no loss, corruption, or mismatch. Proposed
measurement: exact-match rate between expected and restored values across a
labeled test corpus.

### Analytical Fidelity

Whether the AI's analysis of transformed data reaches the same conclusions it
would reach on the original data — trends, computations, and recommendations
should not degrade materially because values were tokenized. Proposed
measurement: comparative evaluation of AI outputs on matched raw vs. transformed
datasets, scored against a rubric or ground truth.

### Latency

The time overhead the transformation and restoration steps add to a normal AI
request. Proposed measurement: end-to-end latency with and without the layer in
the path, across varying dataset sizes.

### Provider Independence

Whether the layer's behavior and guarantees hold consistently when the
underlying AI provider is swapped. Proposed measurement: the same test suite
(restoration accuracy, fidelity) run against multiple providers, compared for
consistency.

### Scalability

How the above dimensions hold up as dataset size, field count, and request
volume grow. Proposed measurement: the same test suite run across a range of
dataset sizes, looking for non-linear degradation.

### Failure Cases

Systematic testing of the scenarios identified in
[`docs/system-boundaries.md`](system-boundaries.md) — exact-value-dependent
analysis, entity resolution, temporal references, complex nested data — to
characterize _how_ the architecture fails, not just whether it does.

### Edge Cases

Malformed input, partially sensitive fields, mixed-language data, ambiguous
classifications, and similar conditions that a general test suite might not
naturally surface.

## Principles for This Framework

- **No cherry-picked results.** Reported evaluation should include the full test
  suite's outcomes, not selected favorable cases.
- **Reproducibility.** Test datasets, methodology, and scoring criteria should
  be published alongside any results, so findings can be independently checked.
- **Negative results are results.** A dimension where the architecture performs
  poorly is exactly as reportable as one where it performs well — see
  [`docs/limitations.md`](limitations.md) for how this connects to the project's
  broader commitment to intellectual honesty.

This framework will be revised as Phase 1–3 of the
[implementation roadmap](implementation-roadmap.md) surface considerations not
anticipated here.

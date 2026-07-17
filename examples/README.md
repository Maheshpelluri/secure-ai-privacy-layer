# Examples

## Current status: planned, not built

There is no working code in this directory. Once a Phase 1 prototype exists (see [`../prototype/README.md`](../prototype/README.md)), this directory is intended to hold illustrative, non-production scenarios showing the transform → analyze → restore pattern applied to representative use cases. None of the descriptions below should be read as claims about what currently works — they describe the kind of scenario each future example would cover and the specific hard cases each sector raises.

## Planned scenarios

### Healthcare
A clinical operations analyst asks an AI platform to summarize patient-visit trends without the model ever seeing patient names, medical record numbers, or dates of birth. Hard case to address: some clinical analysis genuinely depends on exact dates (age at diagnosis, treatment intervals) — see the exact-value dependency limitation in [`../docs/limitations.md`](../docs/limitations.md).

### Finance
An analyst asks for a variance report across client accounts without exposing account numbers or client-identifying transaction detail. Hard case: financial figures often need to remain analyzable at exact precision (totals must still sum correctly after restoration), which constrains how aggressively values can be transformed.

### Education
A researcher or administrator analyzes student performance data without exposing student identity. Hard case: small cohort sizes can make even de-identified data re-identifiable through pattern alone — a limitation of any field-level transformation approach, not specific to this project.

### Legal
A consultant reviews contract terms or case notes with AI assistance without exposing client names or matter-specific identifiers. Hard case: legal text is often narrative and unstructured, making consistent field-level transformation harder than in tabular data — see the multimodal and unstructured-data notes in [`../docs/future-research.md`](../docs/future-research.md).

### Retail
A small business owner analyzes sales and customer data without exposing customer PII to a public AI tool. Hard case: customer analytics often benefit from cross-referencing multiple datasets (purchase history, support tickets, loyalty program), which raises the entity-resolution limitation noted in [`../docs/limitations.md`](../docs/limitations.md).

### Research
An independent researcher analyzes survey or interview data without exposing respondent-identifying detail. Hard case: qualitative, free-text responses are harder to transform consistently than structured fields — another instance of the unstructured-data gap in current scope.

## What an example will need to include, once built

Per the evaluation framework in [`../docs/evaluation-framework.md`](../docs/evaluation-framework.md), each example is intended to document:

- the original (synthetic, non-real) dataset shape,
- which fields were transformed and why,
- the AI-generated analysis on the transformed data,
- the restored output,
- and any known failure or edge case the example surfaced.

## Contributing an example

Proposals for additional scenarios, or critique of the hard cases identified above, are welcome via issues — see [`../CONTRIBUTING.md`](../CONTRIBUTING.md). Please do not submit examples using real, identifiable, or production data of any kind.

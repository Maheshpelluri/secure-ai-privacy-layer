# Design Principles

These principles describe the architecture's intent — the properties any
implementation should preserve — rather than a specific implementation. They are
conceptual commitments, not measured guarantees; see
[`docs/evaluation-framework.md`](evaluation-framework.md) for how they should
eventually be tested, and [`docs/limitations.md`](limitations.md) for where they
are currently hardest to uphold.

## Provider Independence

The layer should not be bound to a single AI vendor or API. Its behavior should
be definable once and apply consistently regardless of which AI platform sits
behind it, so a change in provider does not require a change in privacy
workflow.

## Minimal Exposure

Only the information an AI model needs to perform its specific task should ever
be visible to it. Where structure or pattern is sufficient, the underlying value
should not be exposed. This is a default-deny posture toward exposure, not a
default-allow one with exceptions.

## Analytical Fidelity

Transformation should preserve whatever structural or statistical relationships
the AI model's task depends on — distributions, formats, relative ordering, and
similar properties — even as identifying values are removed. A transformation
that protects data but destroys the analysis is not a solution.

## Reversibility

Original values should be restorable automatically once analysis returns,
without requiring a manual lookup step. The user's final output should be
complete and accurate, even though the AI model never saw the original values.

## Auditability

What was classified as sensitive, what was transformed, and what was restored
should be reviewable after the fact. A privacy claim that cannot be inspected or
verified is not a strong claim.

## Explainability

Why a given value was or was not exposed to the model should be traceable to a
stated rule or classification, not an opaque decision. This matters both for
user trust and for debugging incorrect classifications.

## Workflow Compatibility

The layer should fit around how people already use AI tools — uploading a file,
pasting data, issuing a query — rather than requiring a fundamentally different
workflow or specialized interface to benefit from it.

## Extensibility

The set of data types, sensitivity categories, and AI usage patterns this
architecture handles should be able to grow over time — see
[`docs/future-research.md`](future-research.md) for the categories (multimodal
data, agentic workflows, and others) not yet in scope.

## How These Principles Relate to Each Other

Some of these principles are in tension by design. Minimal Exposure pushes
toward transforming more; Analytical Fidelity pushes toward transforming only
what's safe to transform without breaking the task. Reversibility requires
maintaining a mapping that, if mishandled, would itself become a sensitive
asset. Resolving these tensions correctly, for a given dataset and task, is one
of the central open problems this project has not yet solved — see
[`docs/system-boundaries.md`](system-boundaries.md) and
[`docs/limitations.md`](limitations.md).

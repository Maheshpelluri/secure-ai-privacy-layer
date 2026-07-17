# Implementation Roadmap

This roadmap describes a proposed sequence of phases, not commitments with
dates. No phase beyond Phase 0 has begun. Each phase lists objectives,
deliverables, and the criteria that would indicate it's ready to close — not
results, since none exist yet.

## Phase 0 — Architecture

**Objectives:** Establish the problem, the market gap, the conceptual
architecture, and the design principles clearly enough to support implementation
decisions later.

**Deliverables:** The vision article (`article/index.html`); this documentation
set (`docs/`); explicit system boundaries and threat model.

**Success Criteria:** The architecture can be explained to, and critiqued by,
someone with no prior context, without requiring code to exist. (This phase is
the current state of the repository.)

## Phase 1 — Core Engine

**Objectives:** Build a minimal transformation/restoration engine for a single,
well-defined data format (e.g., tabular CSV data) and a fixed set of sensitive
field types (e.g., names, emails, currency values).

**Deliverables:** A reference implementation of the Classifier, Transformer,
Mapping Store, and Restorer components described in
[`docs/architecture.md`](architecture.md), operating entirely offline (no AI
provider call yet).

**Success Criteria:** Given a sample dataset, the engine can transform sensitive
fields, and restore the original values from the transformed output with no loss
of fidelity, on a defined test set.

## Phase 2 — Provider Integration

**Objectives:** Connect the Core Engine to at least one real AI provider, and
validate that analysis performed on transformed data remains useful once
restored.

**Deliverables:** An integration path for calling a public AI API with
transformed data and mapping the response back through the Restorer;
documentation of what changed in output quality compared to unrestricted access
to raw data, if anything.

**Success Criteria:** A defined analysis task (e.g., summarization, dashboard
generation) produces output of comparable usefulness whether or not the privacy
layer is in the path, evaluated against criteria in
[`docs/evaluation-framework.md`](evaluation-framework.md).

## Phase 3 — Evaluation

**Objectives:** Rigorously test the properties claimed in
[`docs/design-principles.md`](design-principles.md) — restoration accuracy,
analytical fidelity, latency overhead — under real conditions rather than a
single happy-path test.

**Deliverables:** A published evaluation report, including negative results and
the failure cases identified in
[`docs/system-boundaries.md`](system-boundaries.md), tested rather than assumed.

**Success Criteria:** Evaluation results are reproducible by a third party from
the published methodology and test data.

## Phase 4 — User Experience

**Objectives:** Design and build an interface (or integration pattern) that
makes the layer usable without requiring the user to understand its internals —
consistent with the Workflow Compatibility principle.

**Deliverables:** A minimal, usable interface (CLI, library, or lightweight
application) for applying the layer to a real dataset and AI query.

**Success Criteria:** A user unfamiliar with the architecture can complete a
real analysis task using the layer, end to end, without external guidance beyond
the interface itself.

## Phase 5 — Production Readiness

**Objectives:** Address the operational concerns required for real,
non-experimental use: security review of the Mapping Store, performance at
realistic data volumes, provider API changes over time, and formal documentation
of guarantees and non-guarantees.

**Deliverables:** A security review; a documented, versioned interface;
monitoring/observability for the layer itself; a formally maintained
provider-compatibility list.

**Success Criteria:** An independent security review finds no unaddressed
critical issues relative to the threat model in
[`docs/system-boundaries.md`](system-boundaries.md); the project can state, in
writing, exactly what it does and does not guarantee.

---

Phases are expected to surface findings that revise earlier phases, including
this document and the architecture itself. This roadmap is a starting sequence,
not a fixed contract.

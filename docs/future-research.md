# Future Research

The architecture described in this repository focuses on structured, text-based
data and single-turn request/response interactions with an AI model. That scope
was chosen deliberately to keep the initial architecture tractable — see
[`docs/system-boundaries.md`](system-boundaries.md). A number of adjacent areas
are acknowledged as open research rather than solved, deferred, or out of scope
permanently.

## Agentic AI

As AI systems increasingly act autonomously across multiple steps — planning,
calling tools, taking actions — sensitive data may pass through many
intermediate steps rather than a single upload. How a privacy layer should
reason about data flowing through an agent's multi-step plan, rather than a
single request, is unresolved.

## MCP (Model Context Protocol) and Similar Ecosystems

As AI systems connect to external tools and data sources through standardized
protocols, sensitive data may enter an AI workflow from many directions, not
just a user-initiated upload. Whether and how a privacy layer should operate at
this level is an open question.

## Multimodal Inputs

Images, PDFs, audio, and video all carry sensitive information (a photographed
document, a voice recording, a scanned form) in forms the text-based
transformation approach described in [`docs/architecture.md`](architecture.md)
does not address.

## Streaming Data

The current architecture assumes a bounded dataset. Continuous or streaming data
sources raise different questions about when and how transformation and
restoration happen.

## Long-Term Memory and Cross-Session Context

AI systems increasingly retain context across sessions. Whether
previously-transformed data should remain transformed in a persistent memory
store, and how restoration should behave across sessions, has not been designed.

## Tool Calling

Where an AI model itself invokes external tools with arguments derived from data
it has seen, ensuring those arguments don't leak restored values back into an
untrusted context is a distinct problem from the request/response case this
architecture currently addresses.

## Retrieval-Augmented Generation (RAG)

Retrieval systems that pull sensitive documents into a model's context at query
time introduce a data path this architecture has not yet been designed around.

## Observability

What it means to meaningfully observe a privacy layer's behavior in production —
beyond the audit record described in [`docs/architecture.md`](architecture.md) —
including detecting silent failures or classification drift, is unresolved.

## Policy Engines

How organization- or user-defined policies (what counts as sensitive, what's
allowed to be exposed to which provider) should be expressed, versioned, and
enforced is not yet designed.

## Privacy Verification

How a user or auditor could independently verify that a given interaction
actually followed the architecture's guarantees, rather than trusting a
self-reported audit log, is an open and important question — directly related to
the Auditability principle in
[`docs/design-principles.md`](design-principles.md).

## Formal Validation

Whether properties like "no original value crosses Boundary B" can be formally
verified, rather than tested empirically, is a meaningfully different (and
stronger) bar than the evaluation approach described in
[`docs/evaluation-framework.md`](evaluation-framework.md).

---

These areas are listed to be transparent about scope, not to imply near-term
plans to address them. Contributions that explore any of these — even as
analysis without proposed solutions — are welcome; see
[`CONTRIBUTING.md`](../CONTRIBUTING.md).

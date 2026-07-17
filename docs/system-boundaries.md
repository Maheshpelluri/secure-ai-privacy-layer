# System Boundaries

Every architecture has a boundary. This document defines this project's as
explicitly as possible, so its scope is not inferred or assumed.

## What This Project Solves (Proposed Scope)

A conceptual, provider-independent workflow component that reduces the amount of
sensitive information a public AI model needs to see in order to perform
structured data analysis tasks (cleaning, exploration, dashboarding, reporting,
code generation) on a user's behalf, and restores original values in the
resulting output.

## What This Project Does Not Solve

The following are real, adjacent problems that this architecture does not
address. They remain the responsibility of other tools, practices, or system
components:

| Out of scope           | Why                                                          |
| ---------------------- | ------------------------------------------------------------ |
| Prompt injection       | A model-input integrity problem, not a data-exposure problem |
| Model hallucination    | A model-output correctness problem                           |
| AI alignment           | A model-behavior problem, orthogonal to what data it sees    |
| User authentication    | An identity provider's responsibility                        |
| Business authorization | A governance/access-control function's responsibility        |
| Endpoint security      | Device- and OS-level security tooling's responsibility       |
| Network security       | Transport- and network-layer tooling's responsibility        |
| Malware                | Endpoint and network security tooling's responsibility       |
| Data quality           | Data engineering's responsibility, independent of AI use     |

This architecture assumes all of the above are handled elsewhere, and does not
attempt to compensate for their absence.

## Threat Model

**In scope:** an AI provider (or any party with access to what is sent to that
provider) receiving sensitive data as part of a normal, legitimate request, and
that data subsequently being exposed through logging, retention, secondary use,
or breach on the provider's side. The architecture's goal is to reduce what a
legitimately-operating AI provider ever receives, so that this class of exposure
has less to expose.

**Explicitly out of scope:**

- A malicious or compromised user of the system deliberately exfiltrating data
  through the layer itself.
- A compromised Mapping Store (see [`docs/architecture.md`](architecture.md)) —
  its own protection is assumed to be handled by standard access-control and
  encryption practices, not by this architecture.
- An adversarial AI model attempting to infer original values from transformed
  data through statistical inference or repeated querying. This is a genuine,
  unresolved concern — see [`docs/limitations.md`](limitations.md).
- Attacks on the AI provider's infrastructure itself.

## Assumptions

This architecture currently assumes:

1. The environment on the user's side of Boundary A (see
   [`docs/architecture.md`](architecture.md)) is already reasonably trusted —
   this project does not secure that environment.
2. The AI provider is not deliberately hostile — it is treated as an
   untrusted-but-not-adversarial party whose exposure should be minimized, not
   as an attacker to be defeated.
3. The sensitive data in question is primarily structured or semi-structured
   (spreadsheets, exports, text-based records) — see
   [`docs/future-research.md`](future-research.md) for unstructured and
   multimodal data, which is out of current scope.
4. A single request/response interaction is the primary unit of analysis —
   multi-step agentic workflows introduce complexity not yet addressed (see
   [`docs/future-research.md`](future-research.md)).

## Failure Cases

The architecture is expected to be genuinely difficult, not merely inconvenient,
in situations such as:

- Analytical meaning depending on the exact value itself rather than its pattern
  (e.g., a specific date that triggers a specific regulation).
- Entity resolution — correctly recognizing that two differently-formatted
  records refer to the same person or account.
- Temporal or contextual references spanning multiple fields or documents in
  ways a token-level transform doesn't capture.
- Extremely large, deeply nested, or highly domain-specific datasets governed by
  business rules a general-purpose transform wasn't designed around.

These are named here deliberately: an architecture that hides its failure modes
is less trustworthy than one that states them plainly.

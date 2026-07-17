# Architecture

This document describes the conceptual architecture of the Secure AI Privacy Layer at a component and data-flow level. It intentionally does not describe implementation — no transformation algorithm, storage format, or specific technology is prescribed here. See [`docs/system-boundaries.md`](system-boundaries.md) for what is explicitly out of scope, and [`prototype/README.md`](../prototype/README.md) for why an implementation does not yet exist.

## Position in the Workflow

The architecture is defined by where it sits, not by what it's built from: between the point a user or system holds real, sensitive data, and the point that data (or a representation of it) reaches an AI model.

```
User / System Data
        │
        ▼
┌───────────────────┐
│  Privacy Layer     │  ← this project
└───────────────────┘
        │
        ▼
Transformed Dataset
        │
        ▼
   AI Platform  (any provider)
        │
        ▼
   Analysis / Output (on transformed data)
        │
        ▼
┌───────────────────┐
│  Privacy Layer     │  ← restoration
└───────────────────┘
        │
        ▼
Final Output (original values restored)
```

## Components (Conceptual)

These are described as functional roles, not as a proposed codebase structure:

- **Classifier** — identifies which fields or spans in a dataset are sensitive, and of what type (identity, financial, contact, free text, etc.).
- **Transformer** — replaces sensitive values with stand-in tokens, preserving structure, format, and statistical/analytical relationships needed for the AI model's task.
- **Mapping Store** — holds the relationship between original values and their transformed tokens, scoped to the current session or job, so restoration is possible.
- **Restorer** — reverses the transformation on the AI's output, replacing tokens with original values before the result reaches the user.
- **Audit Record** — a log of what was classified, transformed, and restored, sufficient to answer "what did the model see" after the fact.

The Classifier and Transformer operate before data leaves the user's controlled environment; the Restorer operates after the AI's response returns to that same environment. The AI model itself is never a participant in the Mapping Store.

## Data Flow and Trust Boundaries

There are exactly two trust boundaries relevant to this architecture:

1. **Boundary A — User/system environment → Privacy Layer.** Data crosses this boundary in its original, sensitive form. This boundary is assumed to already be inside a controlled environment (the user's machine, the organization's infrastructure, or an equivalent trusted context).
2. **Boundary B — Privacy Layer → AI Platform.** Data crosses this boundary only after transformation. This is the boundary the architecture exists to protect — it is the point at which data leaves the user's control and enters a third party's.

The Mapping Store never crosses Boundary B. This is the architectural property the rest of the design depends on: **the AI model operates entirely on one side of a boundary it cannot see across.**

## Provider Independence

The architecture treats the AI platform as an interchangeable component behind Boundary B, not as a dependency the layer is built around. Any system capable of receiving a structured input and returning a structured output — regardless of vendor, model family, or hosting arrangement — can sit in that position. This is a structural property of where the layer sits, not a claim that has been validated across every provider.

## Separation of Concerns

This architecture deliberately does not attempt to:

- Authenticate users (an identity provider's job).
- Authorize what data a user is allowed to access in the first place (a governance/access-control function's job).
- Secure the network path between components (a transport/network security function's job).
- Evaluate or improve the AI model's reasoning quality (the AI provider's job).

It has exactly one job: minimize what crosses Boundary B, and restore it accurately afterward. See [`docs/design-principles.md`](design-principles.md) for the principles that follow from this scope, and [`docs/system-boundaries.md`](system-boundaries.md) for what is explicitly excluded.

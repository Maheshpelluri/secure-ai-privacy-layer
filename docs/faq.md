# FAQ

Direct answers to the questions this project is asked most often. Where an
answer is a judgment call rather than a settled fact, it's noted as such.

---

**Why not just use Enterprise AI?**

Enterprise AI deployments (dedicated contracts, private endpoints, custom
governance) are a valid and often better-suited answer for organizations that
can afford to build them. They aren't available to most individuals,
freelancers, small businesses, or teams below a certain size or budget. This
project is about the population left out of that answer, not a criticism of it.

**Why not Private LLMs (self-hosted models)?**

Self-hosting avoids exposure by not using a public model at all. It's a
legitimate alternative that trades away the capability, convenience, and pace of
improvement of frontier public models in exchange for full data control. Some
organizations should choose this instead. This project explores a different
tradeoff: keep using public models, change what they're allowed to see.

**Why not DLP (Data Loss Prevention)?**

DLP operates at the network or endpoint boundary — detecting and blocking
sensitive data leaving an environment. It's complementary, not a substitute: DLP
can flag or stop a transfer, but it doesn't transform what's inside a prompt so
the transfer becomes safe to make in the first place.

**Why not AI Firewalls or AI Gateways?**

These typically handle routing, rate-limiting, and policy enforcement for AI API
traffic. A privacy transformation could plausibly run _as a policy inside_ such
a gateway rather than as a competing layer — see
[`architecture.md`](./architecture.md) for how this project positions itself
relative to that category. They solve a different problem (traffic control) than
this project addresses (content transformation).

**Why not CASB (Cloud Access Security Broker)?**

CASBs govern which cloud applications are reachable and how. They don't inspect
or transform the content of a specific request to a specific AI model.
Complementary, not overlapping.

**Can AI providers (OpenAI, Anthropic, Google) just build this themselves?**

They could, and may build comparable controls into their own platforms over
time. A provider-specific control only protects workflows built on that one
provider, though. The case for an independent layer rests on portability (a
workflow survives a provider switch), consistency (one behavior instead of one
per API), and separation of concerns (the provider handles inference; the
privacy behavior is defined by whoever is trusted with the underlying data). See
[`architecture.md`](./architecture.md) for the longer version of this argument.

**Is this another AI model?**

No. It doesn't perform inference, generate text, or replace a model's reasoning.
It transforms data before a model sees it and restores values after the model
responds.

**Is this a chatbot or a product I can use today?**

No. This repository is at the architecture and research stage. See
[`prototype/README.md`](../prototype/README.md) for current status — there is no
working implementation yet.

**Is this production-ready?**

No, and the repository does not claim otherwise. See
[`limitations.md`](./limitations.md) and the
[Current Status](../README.md#current-status) table in the README.

**Does this guarantee privacy or compliance?**

No architecture in this repository has been formally validated against any
compliance standard (GDPR, HIPAA, SOC 2, or otherwise). Whether this approach
could contribute to compliance efforts is an open question, not a claim made by
this project. See [`system-boundaries.md`](./system-boundaries.md).

**What happens to analysis that genuinely requires the real values (e.g., exact
dates for regulatory triggers)?**

This is a known hard case, not a solved one. See
[`limitations.md`](./limitations.md) and the failure cases discussed in the
article's Scope & Boundaries section.

**How is this different from just telling the AI model not to remember or store
data?**

A provider's retention policy governs what happens to data _after_ it's
received. This project is about what the model receives _at all_. The two are
complementary — one doesn't substitute for the other.

**Why publish this before there's any code?**

Because the problem definition, scope, and design principles are the part most
likely to be wrong in ways that are cheap to fix now and expensive to fix after
implementation choices lock them in. Public review at this stage is treated as
more valuable than a rushed prototype. See
[`CONTRIBUTING.md`](../CONTRIBUTING.md).

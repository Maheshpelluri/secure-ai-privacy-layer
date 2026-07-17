# Glossary

**AI Firewall / AI Gateway** — Infrastructure that routes, rate-limits, and enforces policy on traffic to AI APIs. Addresses traffic control, not necessarily what's inside a given request. See [`docs/market-gap.md`](market-gap.md).

**Analytical Fidelity** — The degree to which a transformed dataset preserves the structural and statistical properties an AI model needs to produce useful analysis. A design principle of this project; see [`docs/design-principles.md`](design-principles.md).

**Audit Record** — A log of what was classified, transformed, and restored during a given interaction, intended to make the layer's behavior reviewable after the fact.

**Boundary A / Boundary B** — The two trust boundaries defined in [`docs/architecture.md`](architecture.md): Boundary A is where original data enters the privacy layer; Boundary B is where transformed data leaves the user's control and enters the AI provider.

**CASB (Cloud Access Security Broker)** — A security control providing visibility and policy enforcement over traffic to cloud applications.

**Classifier** — The conceptual component responsible for identifying which fields or spans of a dataset are sensitive, and of what type.

**DLP (Data Loss Prevention)** — Tooling that detects and blocks sensitive data leaving a network or endpoint.

**Mapping Store** — The conceptual component holding the relationship between original values and their transformed tokens, scoped to a session or job, enabling restoration.

**Pseudonymization** — Replacing identifiers with consistent aliases so analysis remains possible without directly exposing identity; distinct from anonymization, which is not reversible.

**Provider Independence** — The property of not being architecturally bound to a single AI vendor or API. A core design principle of this project.

**Public AI** — AI platforms and models generally available to individuals and organizations over the internet (e.g., ChatGPT, Claude, Gemini), as distinct from privately hosted or fine-tuned deployments.

**Restorer** — The conceptual component responsible for reversing transformation on an AI model's output, replacing tokens with original values before the result reaches the user.

**Secure AI Privacy Layer** — The architecture described in this repository: a provider-independent workflow component that minimizes sensitive-data exposure to AI models and restores original values automatically.

**Sensitive Data / Confidential Information** — Data whose exposure carries privacy, confidentiality, compliance, intellectual-property, or reputational risk — used broadly in this repository to include personal, financial, medical, legal, and proprietary information.

**Tokenization** — Replacing a real value with a non-reversible-by-inspection stand-in ("token") that preserves format or structure without revealing the original value directly.

**Transformer** — The conceptual component responsible for replacing sensitive values with tokens prior to sending data to an AI model.

**Trust Boundary** — A point in a system where the level of trust in the data or the party handling it changes. See Boundary A / Boundary B above.

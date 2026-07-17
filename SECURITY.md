# Security Policy

## Current Security Status

This repository currently contains **architectural documentation and research material only**. There is no reference implementation, library, service, or deployable artifact in this repository as of this writing (see [`prototype/README.md`](prototype/README.md)).

As a direct consequence:

- There is no running system to attack, and no CVE process applies yet.
- "Security" at this stage means the integrity and honesty of the architectural claims themselves — see [`docs/system-boundaries.md`](docs/system-boundaries.md) for the threat model this architecture is being designed against, and [`docs/limitations.md`](docs/limitations.md) for what remains unresolved.

This status will be updated as soon as any code, prototype, or deployable component is added to this repository.

## Experimental Nature

Everything in this repository, including the architecture itself, should be treated as **experimental and unproven**. No claim in this repository should be read as a security guarantee. In particular:

- The design principles in [`docs/design-principles.md`](docs/design-principles.md) describe intent, not verified properties.
- The evaluation framework in [`docs/evaluation-framework.md`](docs/evaluation-framework.md) describes how the architecture *should* eventually be measured — it does not contain results, because none exist yet.

## Responsible Disclosure

Once a prototype or implementation exists in this repository, the following will apply and this document will be updated accordingly:

- Security-relevant issues should **not** be filed as public GitHub Issues.
- Reports should instead be sent privately to the maintainers (contact details to be added once a maintainer team and reporting channel are formally established).
- Reporters can expect acknowledgment within a reasonable timeframe and coordinated disclosure once a fix or mitigation is available.

## Reporting a Concern About the Architecture Today

If you've identified a scenario where the *architecture as described* would fail to protect sensitive data in a way not already acknowledged in [`docs/system-boundaries.md`](docs/system-boundaries.md) or [`docs/limitations.md`](docs/limitations.md), please open an Issue using the `architectural-concern` label. This is one of the most valuable contributions this project can currently receive.

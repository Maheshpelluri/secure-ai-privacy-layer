# Market Gap

## Existing Approaches

A number of established practices and product categories already address parts
of the sensitive-data-and-AI problem. None of them are being displaced by this
project; each solves a real, distinct problem.

| Category                       | What it addresses                                               | Where it succeeds                               | Where friction remains                                                           |
| ------------------------------ | --------------------------------------------------------------- | ----------------------------------------------- | -------------------------------------------------------------------------------- |
| Data Governance                | Ownership and usage rules for data across an organization       | Sets clear policy and accountability            | Doesn't stop a well-meaning employee from pasting a spreadsheet into a chat tool |
| Access Control                 | Who can open which datasets                                     | Prevents unauthorized access at the source      | Controls nothing about where authorized data goes next                           |
| Data Masking / Tokenization    | Replacing real values with stand-ins in shared copies           | Removes identity from a dataset copy            | Usually a manual or batch IT process, too slow for a real-time AI query          |
| Pseudonymization               | Consistent aliasing so analysis works without exposing identity | Preserves analytical structure                  | Reversing to real values typically requires a separate manual lookup             |
| Secure Internal Workflows      | Locked-down, approved tooling                                   | Keeps sensitive work inside company walls       | Rarely includes modern public AI assistants                                      |
| Audit Logs & Compliance Policy | Evidence trail of who accessed what                             | Satisfies regulatory and audit requirements     | Records what happened after the fact; doesn't prevent the exposure               |
| DLP                            | Detecting/blocking sensitive data leaving a network or endpoint | Strong at the network/endpoint boundary         | Doesn't inspect or transform what's inside a prompt                              |
| CASB                           | Visibility and control over traffic to cloud applications       | Governs which applications are reachable at all | Doesn't control what's inside an allowed request                                 |
| Private LLM Deployments        | Running a model inside the organization's own infrastructure    | Avoids external exposure entirely               | Requires infrastructure, cost, and expertise most public AI users don't have     |
| AI Gateways / AI Firewalls     | Routing, rate-limiting, policy enforcement for AI API traffic   | Centralizes control over AI traffic             | Typically enforces policy, not data transformation                               |

## Where Friction Remains

Across this list, a consistent pattern emerges: these practices were largely
designed for a world where "sharing data" meant sending it to another internal
system or a vetted vendor — not typing it into a chat interface that forwards it
to a third-party model in real time. That mismatch is where the friction lives,
and it shows up as:

- Manual scrubbing of files before AI use, done ad hoc and unaudited.
- Quiet avoidance of AI tools for real work, undermining the productivity case
  for adopting them.
- Approval bottlenecks when AI use on sensitive data does get formally
  requested.
- Categories of AI-assisted analysis that never get attempted because the prep
  cost is too high.

## Why This Exploration Exists

This project does not propose replacing any of the practices above. It proposes
examining a specific point in the workflow that none of them directly addresses:
**the moment a user, a piece of sensitive data, and a public AI model meet**, in
real time, per request. Where governance sets policy, access control gates
entry, and DLP/CASB police the perimeter, this project is concerned with what
actually crosses into the AI model's input — and whether that crossing can be
minimized automatically, consistently, and across more than one provider,
without requiring the infrastructure that only large enterprises currently
maintain.

See [`docs/architecture.md`](architecture.md) for how the proposed layer is
positioned relative to this gap, and [`docs/faq.md`](faq.md) for direct answers
to "why not just use X instead."

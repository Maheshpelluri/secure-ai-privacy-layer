# Governance

This repository is an architectural research publication. Governance is designed to keep future decisions explicit, reviewable, and consistent with the published architecture.

## Decision Making

- Architectural changes should be discussed in public issues or RFCs before implementation begins.
- Decisions should prefer evidence, reproducibility, and consistency with the system boundaries documented in `docs/system-boundaries.md`.
- When a change alters scope, assumptions, or trust boundaries, it should be treated as a project decision rather than a routine editorial update.

## Architecture RFC Process

1. Open an RFC using `docs/rfcs/RFC_TEMPLATE.md` or a linked issue describing the proposal.
2. Summarize the problem, options considered, tradeoffs, and impact on the roadmap.
3. Invite review from maintainers and contributors with relevant context.
4. Record the decision and rationale once the proposal is accepted, revised, or declined.

## Proposal Lifecycle

- Draft: The idea is being shaped and may be incomplete.
- Review: The proposal is under discussion and may receive revisions.
- Accepted: The proposal is approved for planned work or documentation updates.
- Rejected: The proposal does not fit the current scope or evidence.
- Superseded: A later decision replaces the earlier one.

## Maintenance Notes

This document defines process only. It does not change the architecture, roadmap, or threat model by itself.

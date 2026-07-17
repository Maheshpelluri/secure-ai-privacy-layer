# Problem Statement

## Public AI Adoption

Public AI platforms — ChatGPT, Claude, Gemini, and comparable systems — have become part of everyday knowledge work: drafting, coding, research, analysis, and reporting. Adoption has moved from isolated experimentation toward operational, everyday use across organizations of every size, and by individuals working independently. This is an observable pattern in how these tools are used, not a prediction about the future.

## The Trust Problem

As adoption matures, the constraint that surfaces is not model capability — it's whether real, sensitive data can be used with a given AI platform with confidence. Analysis becomes meaningfully more useful once it touches actual data: real customer records, real financial figures, real internal reports. That same data is, almost by definition, the data an individual or organization has the strongest reason to protect. This tension — between the data that makes AI useful and the data organizations are least willing to expose — is the core problem this project addresses.

## Enterprise AI vs. Public AI

Large enterprises have built a response to this tension over roughly the past decade: dedicated AI governance functions, private model deployments, compliance frameworks (SOC 2, HIPAA, GDPR-aligned programs), and layered security infrastructure specifically designed to let internal teams use AI without exposing sensitive data externally. These capabilities are real, substantial, and expensive to build and maintain — which is precisely why they are concentrated in large organizations.

Startups, consultants, researchers, freelancers, educators, independent analysts, and small businesses use the same public AI platforms, on data that carries comparable sensitivity, without a governance function, a dedicated security team, or a private deployment behind them. The tools are the same; the supporting infrastructure is not.

## The Market Gap

> The intelligence is now available to everyone. Enterprise-grade privacy is not.

This asymmetry is not a claim about any specific vendor's shortcomings — it's a description of how infrastructure typically diffuses: capability arrives broadly and quickly (the models), while the supporting infrastructure that makes that capability safe to use with sensitive data arrives slowly and unevenly (governance, security tooling, private deployments), concentrated wherever there is budget and staff to build it.

## Why Now

Three trends make this gap increasingly relevant rather than a static condition:

1. **Adoption has moved past pilots.** Public AI use is shifting from occasional experimentation to routine, operational reliance — which increases both the volume of sensitive data involved and the cost of continuing to handle it manually.
2. **The manual workaround doesn't scale.** Deleting names and figures from a spreadsheet by hand before using an AI tool is a real, common behavior today — but it is unaudited, error-prone, and increasingly out of step with how much data professionals want AI to touch.
3. **Multi-provider usage is becoming normal.** As individuals and organizations use more than one AI platform, provider-specific privacy controls (where they exist) become a fragmented, inconsistent patchwork rather than a single workflow property.

See [`docs/market-gap.md`](market-gap.md) for how existing practices address parts of this problem today, and where friction remains.

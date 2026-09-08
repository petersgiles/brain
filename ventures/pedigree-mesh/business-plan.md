---
name: pedigree-mesh-business-plan
description: Business plan for Pedigree Mesh — solo-founder, self-funded, agent-governed data trust layer entering via public-sector data scorecards.
---

# Pedigree Mesh — Business Plan

See [concept.md](concept.md) for the underlying architecture. This
document is the venture, not the design.

## One-line pitch
An independently-audited trust layer for data that AI agents consume on
behalf of humans — starting with public-sector compliance data nobody
currently grades honestly.

## Context
Solo venture. Self-funded (no external runway pressure), so the plan
favours patience and a genuine wedge over the fastest possible cash.
No co-founder, no team — factor that into phase sizing, not into
ambition.

## Problem
- AI agents are becoming real market participants — agent-to-agent
  commerce/negotiation protocols are being actively built out through
  2026 — and they need to decide whether to trust a data source before
  acting on it.
- Existing agent protocols (A2A, ACP, MCP) solve transport and
  negotiation mechanics, not governance: none express "who may access
  this, under what proven conditions, with someone accountable."
- Internal data teams cannot be trusted to grade their own data's
  trustworthiness — the incentive is to protect how leadership perceives
  the team, not to report accurately. This is structurally worse in
  underfunded public bodies producing compliance data nobody outside
  ever checks.

## Solution
A domain-curator agent per data domain (provenance: internal, factual),
audited by an independent mesh agent that computes multi-dimensional
pedigree (confidence: external, composed across every domain a Curator
depends on). Full model in concept.md.

## Go-to-market
Not a platform play, and not a sales-led play into a slow procurement
cycle. The wedge is a public scorecard:
- Pick one class of fragmented, public, comparable compliance data —
  multiple jurisdictions/agencies reporting the same kind of thing to a
  low, inconsistent standard.
- Build the minimum Collector + quality-rule checklist + Mesh audit
  needed to score it, honestly, publicly.
- Publish the cross-jurisdiction comparison. Requires no agency's
  cooperation. Guess, not yet validated: most scores will be poor, and
  that gap is itself the story that gets attention.
- Let reputational pressure generate inbound interest from the
  worst-ranked agencies, rather than cold-selling to all of them.
- Convert engaged agencies to a real, paid Curator installation.

## Revenue model
Qualitative only — no financial projections yet, no basis for real
numbers before a pilot exists. Three plausible channels, not mutually
exclusive:
1. **Curator installation/licensing** — a fee to the domain owner (an
   agency, a company) for an installed, maintained Curator plus its
   quality rules.
2. **Consumer-side access fee** — a fee to Consumer-side agents, or their
   principals, for negotiated, audited access to a high-pedigree domain.
3. **Scorecard/audit product** — selling the comparative audit itself to
   a third party who wants the comparison without domain-level
   integration (insurers, researchers, oversight bodies, journalists).

Channel 3 is the cheapest to prove and the natural first revenue — it
requires no partner.

## Competitive landscape
- **Not competitors, substrate**: A2A, ACP, x402, MCP are transport-layer
  protocols (Google, IBM, and the emerging payment-layer standard) — this
  venture rides on top of them, doesn't compete with them.
- **Not yet contested**: the governance/pedigree layer these protocols
  don't express is, per current research (Sept 2026), a named, open gap —
  not claimed by an incumbent yet.
- **Real risk**: large data-platform vendors (e.g. Databricks, Snowflake)
  are already shipping "agentic" data features and could move into this
  exact governance layer once agent-to-agent data trust becomes a
  visible, funded problem. Speed and a genuine first-mover scorecard are
  the defence, not a durable technical moat.

## Risks
- **Composition-rule design is still open** — cap-at-weakest vs weighted
  discount for how pedigree composes across dependencies — affects
  whether domain owners are incentivised to diversify or consolidate
  their upstream dependencies. Needs resolving before a real Curator
  ships.
- **Rating-channel gaming — treat as certain, not hypothetical.**
  Citation-based confidence has a direct, documented real-world
  precedent: the Australian Research Council's Centres of Excellence
  funding process weighted research citation counts, and those counts
  were gamed ludicrously — citation rings, self-citation, reciprocal
  citation between allied institutions. A domain owner running
  sock-puppet Consumer agents to inflate its own pedigree is the same
  attack, and it will be attempted the moment pedigree carries real
  weight. Mitigations borrowed from bibliometrics (weighting a citation
  by the citer's own independently-established pedigree, detecting
  reciprocal/clustered citation patterns) are only partial — the field
  that invented this kind of metric still hasn't solved the gaming
  problem after decades. Anti-gaming design belongs in the first version
  of the citation-feedback mechanism, not a later hardening pass.
- **Solo-founder bus factor** — no team, no immediate revenue pressure,
  which is a strength for patience but a weakness for velocity; scope
  phases accordingly (below).
- **Regulatory/public-sector sales cycles are slow** once past the
  scorecard into a paid Curator installation with an agency — the
  scorecard wedge exists specifically to shorten this by generating
  inbound interest instead of cold outbound.
- **First domain not yet decided.** Asbestos/silica exposure data was an
  illustrative example used to reason through this concept, not a
  commitment — needs a deliberate choice, weighing data availability,
  personal domain knowledge, and how comparable/embarrassing the
  cross-jurisdiction gap is likely to be.

## Phases
0. **Concept modelled** — done (this document + concept.md).
1. **Build the scorecard MVP** — one Collector, one quality-rule
   checklist, one Mesh audit, against one class of public compliance
   data. No partnerships required.
2. **Publish and observe** — see who responds (press, oversight bodies,
   the ranked agencies themselves).
3. **First paid Curator installation** — with whichever engaged agency
   proves the model; resolve the composition-rule and anti-gaming
   questions against a real case rather than in the abstract.
4. **Generalise** — extract the Curator/quality-rule/Mesh-audit pattern
   into a reusable toolkit once proven on one domain, then pick a second
   domain-type.

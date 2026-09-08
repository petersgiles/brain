---
name: pedigree-mesh-concept
description: Agent-governed data mesh — domain curator agents own provenance, an independent mesh audits and computes pedigree, consumer agents negotiate access under a mandate.
---

# Pedigree Mesh — Concept

Working name. A data mesh where domain stewardship, trust auditing, and
consumption are each a distinct agent role, talking over existing
agent-to-agent protocols rather than a bespoke one.

Not a new architecture. This is Data Mesh's four pillars — domain-oriented
ownership, data as a product, self-serve platform, federated computational
governance — with the operating unit changed from a team to an agent, and
governance made continuous instead of a periodic council review.

## Roles

Each role is its own bounded context: a term is authoritative only within
that role's boundary, and the interface between roles is where translation
happens explicitly.

**Collector** — raw ingestion at the edge. Takes in whatever mess arrives,
emits candidate records tagged with a minimal, explicit provenance stub
(source, timestamp, original format). Whether a domain's Collector and
Curator are the same process is a per-domain, explicit decision — never an
implicit side effect of whatever pipeline happens to exist.

**Curator** — owns one Domain.
- Maintains the domain's **provenance**: an internal, factual lineage graph
  (source → transformation → current status). Conflicting source records
  are represented, never silently collapsed into one answer.
- Declares an itemized quality-rule checklist (validation criteria
  specific to its domain-type) and states which items it satisfies — not
  a summary score.
- Declares its own upstream dependency list — every other domain it
  consumes as an input.
- Publishes its guarantees: freshness policy, versioning, conflict
  representation policy.
- Resolves disputes about provenance directly — a claim that a fact in
  the lineage graph is wrong goes back to the authoritative source.
- Negotiates access terms directly with a Consumer's mandate.

Many Curator instances exist across many domains, all satisfying one
shared behavioural contract — swapping one domain's Curator implementation
for another must never surprise a Consumer already dealing with a
different domain's Curator.

**Mesh** — external to every Domain, by design.
- Owns and audits the quality-rule checklists per domain-type. A Curator
  cannot self-certify against its own checklist — the standards-body
  function folds into the Mesh, and it audits, it doesn't just recommend.
- Computes and publishes **pedigree**: a confidence judgement built from
  (a) a domain's own validation-checklist completeness, (b) the
  recursively composed pedigree of every domain it depends on, and (c) an
  accruing forward-time signal from Consumer citation/usage (see below —
  the most gameable of the three). A domain cannot launder a weak upstream
  dependency into an apparently strong downstream product. Open design
  question: does pedigree cap at the weakest upstream link (SLSA-style),
  or degrade as a weighted discount?
- Pedigree is multi-dimensional, not a single score — different Consumer
  needs (legal-compliance-fitness, scientific-accuracy-fitness,
  freshness-fitness) are independently relevant; collapsing them into one
  number hides the specific reason for confidence.
- Discovery/routing: takes an ambiguous "feel for" request from a Consumer
  and matches it to the right Curator(s), then steps back — negotiation
  happens directly between Consumer and Curator, never through the Mesh.
- Must report honestly even when the finding is unflattering — "this
  domain scores 1 of 15" is a valid, required output. The Mesh is never
  incentivised to flatter a domain it audits, or the pedigree signal is
  worthless. Pedigree lives outside the domain it judges specifically so
  a Curator can never grade its own homework — the same failure mode as
  an internal data team optimising for how leadership perceives it
  instead of for correctness.

**Consumer** — an agent acting under a **mandate**: a scoped grant of
authority from whatever principal (human, org, regulator) it represents.
Not an intrinsic property of the agent — presented at negotiation time.
Queries and disputes facts directly with a Curator. Submits satisfaction
ratings, tagged by need-dimension, to the Mesh — these feed pedigree over
time (a citation/confidence flywheel: better-curated domains get cited
more confidently, raising their pedigree, attracting more citation).

## Provenance looks backward, pedigree accrues forward

Two different temporal directions, not a coincidence of naming:

- **Provenance is backward-looking and fixed.** The evidence trail to
  origin — source, transformation, current status — settled the moment a
  fact enters the domain. It doesn't grow over time; it's traced, not
  earned.
- **Pedigree is forward-accruing and never finished.** A track record
  built from what happens *after* the data exists — most concretely,
  whether Consumers keep citing it with confidence over time, the same
  way a paper's citation count only exists and grows after publication.
  This makes pedigree structurally different from provenance, not a
  different scale of the same thing: it can't be computed once and
  cached, it has to be watched.

So pedigree has three inputs, not two: (a) own validation-checklist
completeness, (b) composed upstream pedigree, and (c) this accruing
forward-time citation/usage signal. (c) is the strongest evidence of real
trust and also the most gameable — see below.

This mirrors a real, documented failure mode: the Australian Research
Council's Centres of Excellence funding process weighted research
citation counts heavily, and citation counts got gamed ludicrously —
citation rings, self-citation, reciprocal "gift" citations between allied
institutions. A forward-accruing confidence signal built from citation/
usage is the same mechanism and inherits the same vulnerability. Not a
hypothetical risk — see [business-plan.md](business-plan.md).

## Why the protocol layer isn't the opportunity

A2A (Google), ACP (IBM), x402 (payment), MCP (tooling) already contest
agent-to-agent transport and negotiation mechanics — not worth competing
on directly. The documented gap, as of Sept 2026, is governance semantics:
expressing and enforcing who may access what, under what proven
conditions, with someone accountable, revocably and auditably. None of
the current protocols express this. That's the actual wedge.

## Go-to-market mechanism

The audit/scorecard doesn't need any domain owner's buy-in to exist.
Illustrative example (asbestos/silica exposure data — used to reason
through this, not a commitment to that domain): most of this class of
data is scraped from glossy annual compliance PDFs produced by
underfunded statutory authorities to tick a reporting box, with zero
information about its own quality.

1. Build a Collector against a class of public, fragmented, comparable
   compliance data — many jurisdictions/agencies reporting the same kind
   of thing, badly, differently.
2. Define a minimal quality-rule checklist for that domain-type.
3. Run the Mesh's audit, honestly, even if every jurisdiction scores
   badly.
4. Publish the resulting cross-jurisdiction scorecard. No agency
   partnership required to produce it.
5. Public, comparable visibility creates its own reputational pressure —
   nobody wants to be the visibly worst-ranked jurisdiction. That's the
   actual sales channel: agencies that rank poorly become the inbound
   prospects, not cold-call targets.
6. Install a real Curator, with real quality rules, for agencies that
   engage. Pedigree for their domain rises over time as Consumers cite it
   more confidently — the flywheel above, now running for real.

See [business-plan.md](business-plan.md) for the venture built on this.

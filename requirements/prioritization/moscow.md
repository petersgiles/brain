---
name: moscow
type: framework
description: MoSCoW sorts requirements into Must/Should/Could/Won't have, so a burndown has an explicit, agreed cut line instead of one flat backlog.
---

MoSCoW buckets every requirement into exactly one of four priority tiers:

- **Must have** — critical; the delivery isn't viable without it.
- **Should have** — important, but the delivery can ship without it if
  it has to.
- **Could have** — desirable, included only if time/budget allows.
- **Won't have (this time)** — explicitly out of scope for this
  delivery, not forgotten — parked, not rejected.

**Why it matters:** a flat backlog hides the fact that not every item
carries the same weight. Naming the cut line explicitly — everything
below "Should" is the first thing to drop under pressure — turns an
implicit, contested judgement call into an agreed, visible one made
before the pressure hits.

**How to apply:** assign a MoSCoW tier per requirement (each one already
written in [[ears-syntax]]) when building a burndown. Revisit the tiers
when scope or timeline changes — a tier is a decision made against
current constraints, not a permanent property of the requirement.

---
name: registry-and-compose
type: pattern
description: When many independent sources must merge into one record per entity, split the registry by contribution shape and compose deterministically.
---

[[self-registering-unit]] works when units are independent and never need
merging. When many independent sources instead need to merge into *one
canonical record per entity*, split the registry by contribution shape:

- Sources that contribute **attributes of one entity** (1:1 properties).
- Sources that contribute **relationships between two entities** (N:M edges).

Run every registered source through one deterministic compose step. The
critical rule: an entity comes into existence the moment **any** source
mentions it — by attribute or by relationship — never gated on one
privileged source's success. (This is [[explicit-modeling]] applied to
entity existence specifically.)

Document the field-collision policy explicitly rather than leaving it
implicit — e.g. last-registered-source-wins, same semantics as a map
literal — and call it exactly what it is: simple and unrefined. Don't
design real conflict resolution before a real conflict has actually
happened; revisit then.

**Where it fits:** any case where "the entity" is really defined by the
union of everything anyone knows about it, and no single source should be
allowed to gatekeep that.

**Where it strains:** entities not keyed by a single identifier or a pair
of identifiers (e.g. a higher-level rollup spanning many entities) need a
third contribution shape, not a forced fit into attribute/relationship.

Related: [[typed-projection-at-wire-boundary]] (what has to happen before
the composed, loosely-typed result is safe to expose externally),
[[explicit-modeling]].

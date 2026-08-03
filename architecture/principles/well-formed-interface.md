---
name: well-formed-interface
type: principle
description: Anything a system exposes as a unit — an API, a service, a module — should be discoverable, addressable, understandable, trustworthy, natively accessible, interoperable, valuable alone, and secure.
---

Anything a system exposes as a consumable unit — a public API, a backing
service, an internal module, a literal data product — should meet the
same eight quality facets. Borrowed from the Data Product Canvas, but not
data-specific: they're a general bar for anything one part of a system
hands to another.

- **Discoverable** — a consumer can find out this thing exists and judge
  whether it fits their use case, without tribal knowledge.
- **Addressable** — it has a single, stable, permanent address (a URL, an
  import path, an endpoint) that reaches it directly.
- **Understandable (self-describing)** — its purpose, shape, and usage are
  documented at the thing itself: what it's for, what each field or
  parameter means, how to call it, ideally with a worked example.
- **Trustworthy** — it states its own guarantees (uptime, latency,
  freshness, versioning policy) and actually holds to them, so a consumer
  can build on it with confidence instead of hedging against it.
- **Natively accessible** — each consumer persona gets the interface that
  actually fits how they work: a UI for an operator, a typed client for
  another service, a CLI for automation — not one format forced on
  everyone.
- **Interoperable (composable)** — it combines cleanly with other units
  (joined, filtered, chained) using standard keys and access patterns,
  regardless of which team owns it.
- **Valuable on its own** — it represents one cohesive concept and is
  useful by itself, without forcing a consumer to also pull in several
  other things just to make sense of it.
- **Secure** — access is authorised and, where warranted, encrypted; this
  is [[boundary-validation]] applied to *who* may consume the unit at all,
  not just what data they send it.

Not every facet carries equal weight for every unit — an internal helper
module cares less about "natively accessible" than a public API does —
but all eight are worth checking against deliberately, not just "does it
work."

**Why it matters:** the eight facets are one idea seen from different
angles — a well-formed interface's cost is paid once, by its owner,
instead of being re-paid by every consumer who has to guess its shape,
hunt for it, or build around a broken guarantee. Skipping a facet doesn't
remove that cost, it just moves it onto someone else, later, usually with
less context than the owner had.

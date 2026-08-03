---
name: uniform-self-registering-interface
type: standard
description: Every self-registering unit exposes the same minimal method surface, so the composition root can treat every unit identically.
---

Self-registering units ([[self-registering-unit]]) expose a uniform,
minimal method surface — identity, declared config needs, what the unit
registers or renders, and a self-registration call — so the composition
root can treat every registered unit identically regardless of what it
does internally.

Typical shape: `Name()`, `Config()` (declared requirements, folded into
[[config-loader-chain]]), whatever the unit contributes (`Views()`,
`Routes()`, `Nav()` — plural, since a unit may contribute nothing for an
optional piece and that's a valid, explicit "no"), and `Register(deps)`
taking a [[dependency-struct-not-positional-args]].

**Why it matters:** a uniform interface is what makes the composition
root's loop over "all registered units" possible at all — the moment one
unit needs a bespoke method signature, it either breaks the loop or forces
every other unit to grow an unused method to match.

---
name: explicit-modeling
type: principle
description: Don't let an entity's existence or a rule about it be an implicit side effect of which field happens to be populated — represent it explicitly.
---

Don't let an entity's existence, or a rule that applies to it, be an
implicit side effect of "whichever field happens to be populated" or "which
loop happens to iterate over it." If something is true, represent it as a
named field or an explicit branch in the code — not as an emergent property
of incidental control flow.

A common failure shape: a system's model of "does X exist" is silently
defined as "did the first, most obvious data source have a row for it" —
and anything real that lacks *that specific* row vanishes without an error,
because nothing ever explicitly asked "does X exist by any other means."
[[registry-and-compose]] is the pattern that fixes this: an entity exists
the moment *any* registered source mentions it, not just the historically
first/most-obvious one.

**Why it matters:** implicit rules are invisible until something violates
them, and then they look like silent, causeless bugs — the code has no line
you can point to that says "this is why." An explicit model gives you that
line.

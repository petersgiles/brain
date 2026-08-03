---
name: law-of-demeter-across-layers
type: principle
description: A layer talks only to its own immediate neighbor — never reaches through a peer into that peer's internals just because it's technically reachable.
---

A layer talks to its own immediate neighbor only — its own local service,
its own adjacent API — and never reaches *through* a peer into that peer's
internals (its database, its disk, its private state), even when nothing
technically stops it.

Concretely: if layer B exposes an API in front of its storage, layer A calls
B's API. A never opens B's database directly, even if it has the
credentials and it would save a network hop. The hop is the point — it's
what keeps B free to change its internals without breaking A.

**Why it matters:** this is what makes [[layered-authority]] enforceable in
practice rather than just declared in a diagram. The moment one layer
back-doors into another's internals, the "authoritative layer" stops being
authoritative — there are now two paths to the same data, and they will
diverge under exactly the same conditions [[single-source-of-truth]] exists
to prevent.

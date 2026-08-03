---
name: layered-authority
type: principle
description: One layer is authoritative for a given piece of state; every other layer holds a view of it, never a second copy.
---

One layer in a system is authoritative for a given piece of state. Every
other layer holds a *view* of that state — a read, a cache, a projection —
never an independent second copy that could disagree with the original.

A layer answers "what do I know about myself or the system" by asking the
authoritative layer, not by independently reading the same raw inputs (env
vars, disk, another layer's storage) that the authoritative layer already
reads. Two code paths deriving the same fact from the same raw source is
exactly how the two paths quietly diverge later.

**Why it matters:** when authority is unambiguous, "where do I go to fix
this" has one answer. When it's smeared across layers, a bug fix in one
place doesn't fix the other copy, and nobody notices until they disagree in
production.

See also: [[single-source-of-truth]], [[law-of-demeter-across-layers]],
[[decide-once-at-the-authority]].

---
name: narrow-role-specific-interfaces
type: principle
description: Expose narrow, consumer-specific interfaces instead of one general-purpose interface covering every consumer's needs — a change to capability one consumer doesn't use shouldn't touch the others.
---

Expose narrow, role-specific interfaces rather than one general-purpose
interface that bundles every capability any consumer might ever need. A
consumer should depend only on the surface it actually uses — not be
handed (and forced to implement, mock, or merely tolerate) a dozen
unrelated methods because they happen to live on the same fat interface.

Concretely: if one interface serves a reader that only ever calls three of
its twelve methods and a writer that needs a different four, split it —
`Reader`/`Writer` (or narrower still), not one `Store` interface with all
sixteen. A change to the other nine methods now can't force the reader's
implementations to change, be re-mocked, or even recompile.

This is [[minimal-necessary-abstraction]] applied to interface shape
specifically: don't design one interface wide enough to cover a
hypothetical future consumer's needs today. It's also
[[well-formed-interface]]'s "valuable on its own" facet seen from the
provider's side — the interface itself should be a cohesive concept, not a
grab-bag that happens to be convenient to declare in one place.

**Why it matters:** a fat interface couples consumers to each other through
the interface even when their actual needs never overlap — one consumer's
new requirement forces every implementer to grow a method the others don't
want, and every implementer's mock has to fake methods it never calls.

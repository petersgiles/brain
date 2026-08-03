---
name: extract-after-duplication-proves-itself
type: principle
description: Extract a shared library only once two real, independent codebases share near-identical scaffolding that has already drifted — not preemptively.
---

Don't pre-build a shared library for a second project that doesn't exist
yet. Once two real, independently-evolving codebases turn out to share
near-identical scaffolding — and it's provably already drifted (a stray
hardcoded value surviving from a copy-paste origin, a fix applied to one
copy and forgotten in the other, a security hole closed in one and left
open in the other) — that's the actual signal to extract.

When extracting: lift out the parts that are already identical and
decoupled first (pure lift-and-shift, low risk). Defer the parts that need
real generalization (provider-specific auth, storage backends) until a
second real consumer exists to validate the generalized shape against —
don't guess at the general shape from a single example.

This is [[rule-of-three]] and [[minimal-necessary-abstraction]] applied at
the scale of whole codebases rather than individual functions.

**Why it matters:** premature extraction guesses at a general shape from one
data point and usually guesses wrong; the guessed abstraction then has to
be reworked anyway once a second real consumer shows up, at higher cost
than if extraction had simply waited.

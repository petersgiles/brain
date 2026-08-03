---
name: layered-trust-guards
type: pattern
description: Model each distinct caller trust class as its own narrow guard checking one condition, ordered from least to most trusted.
---

When callers fall into distinct trust classes — anonymous, peer/internal,
authenticated, elevated/admin — model each as its own narrow
guard/middleware that checks exactly one condition, ordered from least to
most trusted. Compose each route from the *narrowest* guard that satisfies
its actual requirement.

Never reuse a broader, lower-trust guard on a route just because it happens
to pass — especially not on anything that mutates state. A relaxed guard
built to unblock one specific low-stakes read (e.g. "can this caller check
whether a resource already exists, before it has full credentials for it")
should be documented as carrying lower trust than the standard guard, and
never quietly reused elsewhere because it's already there and convenient.

**Why it matters:** trust checks that are correct individually but get
casually reused outside their original justification are how privilege
creeps in gradually, one "it already sort of works" shortcut at a time.

Related: [[guards-named-for-the-check]] (the naming standard this implies),
[[guard]] (glossary), [[boundary-validation]].

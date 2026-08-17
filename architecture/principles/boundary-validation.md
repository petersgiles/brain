---
name: boundary-validation
type: principle
description: Validate and sanitise at the edges of the system; trust internal calls between your own layers instead of re-checking everywhere.
---

Validate and sanitise at the edges of the system — user input, external
systems, deserialised payloads. Internal calls between your own layers
trust each other's guarantees; don't defensively re-validate the same
condition at every hop just because it's cheap to add a check.

This pairs with [[fail-fast-no-fallbacks]]: the boundary is exactly where
fast failure belongs. It's also why [[minimal-necessary-abstraction]] steers
away from adding validation "just in case" deep in the call stack — if a
precondition really can't happen once the boundary has checked it, coding
as if it could happen is dead weight, not safety.

**Why it matters:** validation scattered through every layer is expensive to
maintain and gives false confidence — it's easy for the *real* boundary
check to be missing precisely because every internal layer looks like it's
"handling" the bad-input case somewhere.

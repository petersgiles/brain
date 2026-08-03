---
name: fail-fast-no-fallbacks
type: principle
description: Required configuration and inputs are validated once at the boundary; missing or bad values halt loudly right there, never silently default.
---

Required configuration and inputs are validated once, at the boundary
(startup for config, the edge of a request for input), and a missing or bad
value halts things loudly, right there. Never swallow an error silently,
and never return null or a zero value to paper over a problem — that just
moves the failure three layers downstream, where it's confusing and
disconnected from its actual cause.

Only catch an error where you can genuinely recover from it. Otherwise, let
it propagate (log-and-rethrow at most) rather than absorbing it into an
empty catch block.

The concrete mechanism for the config half of this is
[[config-loader-chain]]: one place declares every required value, and
startup refuses to proceed if any are missing.

**Why it matters:** a system that fails loudly at the true point of failure
is trustworthy — you can act on its errors. A system that silently defaults
accumulates small wrongnesses that surface later, unrelated-looking, far
from their cause.

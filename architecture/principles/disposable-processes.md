---
name: disposable-processes
type: principle
description: A process starts fast enough to feel instant and shuts down gracefully on a termination signal — finishing in-flight work and releasing resources — rather than being killed mid-operation.
---

A process should be startable and stoppable at any moment for negligible
cost. Startup gets the process ready to serve almost immediately —
expensive one-time work (cache warming, precomputation) happens lazily or
in the background, not on the critical path to "ready." Shutdown responds
to a termination signal by finishing in-flight work, releasing connections
and file handles, and exiting promptly — not by being killed mid-operation
because nothing was listening for the signal.

This is a lifecycle property, not a performance target: the point isn't
"fast" for its own sake, it's that starting and stopping the process is
boring and safe enough to do often, on purpose, without an operator
flinching.

**Why it matters:** fast, graceful start/stop is what makes horizontal
scaling, rolling deploys, and crash recovery cheap and routine instead of
risky. A process that takes 30 seconds to become ready, or that ignores a
termination signal and gets hard-killed, turns every deploy or autoscale
event into something that can lose work or degrade the service — the
operational cost compounds with every restart, not just the slow ones.

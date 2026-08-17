---
name: economise-programmer-time
type: principle
description: Programmer time is the expensive, scarce resource; machine time is cheap — when a design choice trades one for the other, default to spending machine time.
---

Programmer time is expensive; machine time, for almost all applications,
is not. Unix tradition calls this the Rule of Economy. When a design
choice trades one for the other — a higher-level language with automatic
memory management over a lower-level one, a slightly less CPU-efficient
approach that's dramatically simpler to write and maintain — default to
spending machine time, not programmer time, unless there's a demonstrated,
measured reason not to.

This is the resource-allocation argument underneath several other
principles rather than a separate technique: it's why
[[minimal-necessary-abstraction]] favors duplication over a guessed-at
abstraction (the abstraction costs programmer time now, for a maybe-never
payoff), and why [[prototype-before-polishing]] defers optimization until
it's proven necessary (tuning is programmer time spent on a machine-time
problem that, most of the time, doesn't exist yet).

**Why it matters:** it's easy to default to optimizing whatever's easiest
to measure — CPU cycles, memory, disk — because it's visible on a
dashboard. Programmer time spent debugging, maintaining, and re-learning
complex code is just as real a cost, just harder to see on the same
dashboard.

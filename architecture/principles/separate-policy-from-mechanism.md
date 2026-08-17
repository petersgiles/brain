---
name: separate-policy-from-mechanism
type: principle
description: Policy (what to do, which changes fast) and mechanism (how it's done, which should be stable) mutate on different timescales — hardwiring them together makes policy rigid and destabilises mechanism whenever it changes.
---

Separate policy from mechanism: separate the interface that decides *what*
happens from the engine that carries out *how*. Unix tradition calls this
the Rule of Separation — the canonical example is a windowing system that
is a generic graphics engine (mechanism), with look-and-feel left to
toolkits built on top of it (policy).

Policy and mechanism mutate on different timescales — policy changes
fast, mechanism should stay stable — so hardwiring them together has two
bad effects: it makes policy rigid and hard to change in response to real
requirements, and it means every policy change risks destabilizing the
mechanism underneath it. Separating them lets you experiment with new
policy without touching the mechanism, and makes the mechanism far easier
to test, since its tests don't need to account for policy that changes out
from under them.

[[one-composition-root]] is one concrete instance of this split: the root
is where policy (which concrete implementation to use) is decided, once,
and injected into mechanism (the rest of the code) that neither knows nor
cares which concrete choice was made.

**Why it matters:** when policy and mechanism are tangled together, every
change to "what the user sees" carries the risk of breaking "how it
actually works" — and vice versa — even though the two should be able to
change completely independently.

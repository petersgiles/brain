---
name: prototype-before-polishing
type: principle
description: Get a design working end-to-end, un-optimised, before tuning it — premature optimization routinely locks in the wrong design and wastes effort no profile ever asked for.
---

Prototype first, then polish. Get something working before you optimise
it. Unix tradition calls this the Rule of Optimization, and it shows up
independently in Kernighan & Plauger ("90% of the functionality delivered
now is better than 100% delivered never") and Knuth ("premature
optimization is the root of all evil").

[[design-sketch-before-code]] is the concrete mechanism this repo already
uses for the design half of this — write the interface sketch and the
honest fit/strain section before implementing, rather than trying to
anticipate every case up front. The optimization half is the same idea
applied after something works: don't tune for speed until you've measured
where the actual bottleneck is, and even then, only tune the part that
provably dominates — fancy algorithms are usually slower than simple ones
at the sises that actually occur in practice, and always buggier.

Prototyping also has a second, easy-to-miss payoff: it's often what shows
you which features you don't have to build at all. The most powerful
optimization tool is frequently the delete key, not a faster algorithm.

**Why it matters:** optimizing before the real bottleneck is known
routinely optimises the wrong thing, at the cost of transparency and
simplicity elsewhere in the design — and a premature local optimization
often blocks a much bigger global optimization that would have been
obvious once the whole thing actually worked.

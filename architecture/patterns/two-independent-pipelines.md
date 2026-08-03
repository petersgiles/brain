---
name: two-independent-pipelines
type: pattern
description: When two surfaces render "the same" data via different mechanisms, give each its own end-to-end pipeline rather than sharing one derived state.
---

When two different surfaces need "the same" filtered/derived data but are
rendered by fundamentally different mechanisms — a live interactive canvas
versus a periodically-refreshed server-rendered fragment, say — give each
surface its own end-to-end pipeline from source to render, each owning its
own refresh trigger and its own render step, rather than computing one
shared derived state and fanning it out to both renderers.

A shared intermediate that two independently-timed refresh loops both
consume tends to race and go stale — one loop swaps its rendering out from
under the other's read of the shared state, producing an inconsistent
result that's hard to reproduce because it depends on timing. Two
pipelines that each own their cadence end-to-end don't have this failure
mode, at the cost of the two surfaces being allowed to be momentarily
inconsistent with each other — an acceptable tradeoff when each surface's
correctness only depends on its own pipeline.

**Where it strains:** if the two surfaces must always show byte-identical
state (not just "the same underlying data, refreshed independently"), this
pattern is wrong — that case genuinely needs [[single-source-of-truth]]
enforced through one shared pipeline instead.

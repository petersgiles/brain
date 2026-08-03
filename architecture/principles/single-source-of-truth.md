---
name: single-source-of-truth
type: principle
description: State that multiple consumers react to lives in exactly one place; consumers subscribe or query, never maintain their own derived copy.
---

State that multiple consumers need to react to lives in exactly one place.
Consumers subscribe to it or query it on demand — they never maintain their
own derived copy of it "for convenience," because a derived copy is a second
truth waiting to drift from the first.

This is [[layered-authority]] applied specifically to *shared, reactive*
state (as opposed to authority over a whole domain concept). The pattern
[[single-observable-stream]] is the concrete client-side mechanism for
enforcing it: one writer, many subscribers, never a second independently
maintained copy of the same data.

**Why it matters:** every place a value is duplicated is a place someone can
update one copy and forget the other. Bugs of this shape are notoriously
hard to reproduce because they only show up when the copies have already
diverged.

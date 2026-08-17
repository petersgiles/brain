---
name: scoped-extensibility
type: principle
description: Data and wire formats you don't fully control the evolution of should be self-describing (versioned, or composed of droppable/addable clauses) — this is narrower than "design for the future" and doesn't license building unused generality elsewhere.
---

Design formats and protocols to be extensible. Unix tradition calls this
the Rule of Extensibility: when you design a data format or a protocol,
make it self-describing enough to grow — a version number, or a structure
built from self-contained clauses that can be added or dropped without
confusing whatever reads it. The payoff shows up later, when the format
needs to change and you're not locked into an early choice you can't
revise without breaking every existing reader.

**This is deliberately narrower than the source rule's own framing.** The
original states it broadly — "design for the future, because it will be
here sooner than you think," organise code so new functions can be
plugged in without rebuilding the architecture. Read that broadly, it
directly contradicts [[minimal-necessary-abstraction]] and
[[extract-after-duplication-proves-itself]], both of which hold that
building for a guessed-at future case is usually a bet that loses: the
guessed shape doesn't match the real second case when it arrives, and the
unused generality was pure cost in the meantime.

The part of this rule that holds up without that conflict is narrower and
specifically about **formats and contracts you don't fully control the
future evolution of** — a wire format, a config schema, a public API
response, anything with readers you can't update in lockstep with writers.
There, self-description is cheap to add up front and expensive to retrofit
after real consumers exist, which is the opposite cost profile from
speculative code abstraction. [[semantic-versioning]] is this repo's
concrete mechanism for the versioning half. Outside that narrow case —
internal code, single-consumer data — [[minimal-necessary-abstraction]]
is still the rule: don't add extension points for a plugin architecture
nobody has asked for yet.

**Why it matters:** the two principles aren't actually in tension once
scoped correctly — they agree that speculative generality is a cost paid
now for a guessed-at, probably-wrong future. They disagree only on formats
with independent readers and writers, where "wrong guess about the future"
is cheap to hedge against (a version field) and "no hedge at all" is
expensive to fix later (every existing reader breaks at once).

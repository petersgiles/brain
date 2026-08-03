---
name: single-observable-stream
type: pattern
description: Client-side state that multiple UI parts react to is exposed as one subscribable stream with exactly one writer.
---

Client-side state that multiple UI parts must react to is exposed as one
subscribable stream or store, with exactly one writer. Consumers subscribe
rather than polling or reading ambient globals — this is what keeps "who
changed this and when" answerable, since there is exactly one code path
capable of changing it.

This is the concrete client-side mechanism for
[[single-source-of-truth]]: the principle says "don't maintain a second
copy," this pattern is *how* you make that structurally true instead of
just a convention people are trusted to follow.

Related: [[two-independent-pipelines]] — note the distinction: this pattern
is about *one* pipeline having exactly one writer internally; that pattern
is about *deliberately* not sharing state between two different pipelines
serving two different rendering targets. They're not in tension — apply
this pattern within each of the pipelines from that one.

---
name: uncertainty-travels-with-the-value
type: principle
description: When a value is inferred or defaulted rather than observed, carry that fact as an explicit typed signal — never present a guess as a fact.
---

When a value is inferred, defaulted, or synthesised rather than directly
observed, that fact travels with the value as an explicit, typed signal —
never presented indistinguishably from a real, observed value.

The concrete mechanic is [[inferred-values-get-their-own-field]]: a sibling
boolean or flag, not an overloaded meaning packed into the same field.

**Why it matters:** a guess dressed as a fact is a worse failure mode than a
visible gap. A visible gap prompts someone to go find the real data; a
silent guess gets trusted, propagated, and acted on as if it were ground
truth, and the eventual discovery that it wasn't tends to be expensive and
hard to trace back.

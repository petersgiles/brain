---
name: inferred-values-get-their-own-field
type: standard
description: Never overload one field to mean both "observed" and "synthesized" — add a sibling boolean/flag instead.
---

Never overload one field to mean both "this was directly observed" and
"this was inferred/defaulted/synthesized." Add a sibling boolean or flag
field instead, and carry it all the way to wherever the value is presented,
so a renderer can distinguish the two cases rather than treating them
identically because the type system can't tell them apart.

This is the concrete mechanism for
[[uncertainty-travels-with-the-value]] — the principle says the fact must
travel with the value; this is the specific, boring way to do that in a
typed contract rather than via an undocumented sentinel value or a
side-channel the consumer has to know to check.

**Why it matters:** a magic sentinel (like a specific numeric value meaning
"unknown") is exactly the kind of implicit rule
[[explicit-modeling]] warns against — it works until someone forgets it's
magic and treats it as real data.

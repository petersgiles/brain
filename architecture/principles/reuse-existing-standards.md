---
name: reuse-existing-standards
type: principle
description: Before designing a bespoke format, protocol, or data model, check whether an existing standard already fits the problem — adopt only the slice you need now, and keep the seam open for the rest.
---

When a problem space already has an established standard — a data model,
wire format, protocol, or vocabulary — check whether it fits before
inventing your own. An existing standard usually encodes hard-won
decisions about the shape of the problem: which fields matter, which
cases earlier, narrower attempts missed, what implementations elsewhere
already expect to see. Reinventing that shape from scratch throws away
that accumulated knowledge and produces a private format that nothing
else can read.

This isn't licence to pull in a standard wholesale — its full protocol
stack, its transport, every optional feature it defines — just to borrow
a shape. Adopt only the slice that fits today's use case, usually the
data model or vocabulary, not necessarily the wire protocol or governance
around it. [[minimal-necessary-abstraction]] still applies to the parts
you didn't need: don't build out the rest of the standard "in case" it's
wanted later. What's worth doing instead is leaving a deliberate seam
where the unused part would plug back in — a naming choice that mirrors
the standard's own, a note about which part was skipped — so it can be
reintroduced cheaply if the need becomes real, rather than requiring a
redesign.

**Why it matters:** a bespoke shape is a private dialect — every consumer
who wants to interoperate with the wider ecosystem the standard
represents has to translate to and from it by hand, and that cost is paid
repeatedly, by everyone who integrates, instead of once by the format's
own designer. [[well-formed-interface]]'s interoperable facet is the
receiving end of this: a format that already speaks a known standard is
interoperable by construction; one that doesn't has to earn
interoperability after the fact through adapters. [[scoped-extensibility]]
is the versioning half of the same instinct — that principle hedges the
shape you did invent, this one is about not needing to invent the shape
in the first place.

This pairs with [[distrust-one-true-way]] read in the other direction:
don't assume the standard is a perfect fit either — its designers didn't
anticipate your case any more than you can anticipate the future. Check
the fit before adopting; don't adopt purely out of an instinct to avoid
looking like you reinvented something.

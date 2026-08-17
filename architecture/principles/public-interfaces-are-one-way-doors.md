---
name: public-interfaces-are-one-way-doors
type: principle
description: The moment an interface has a real consumer outside your control, removing or restructuring it is no longer your unilateral decision — shipping it is the commitment, not a later version bump.
---

The moment an interface — a CLI flag, an endpoint, a config key, a public
function signature — has a real consumer you don't control, you've lost
the ability to unilaterally remove or restructure it. You can almost
always *add* to it without breaking anyone. You can almost never *remove*
or reshape part of it the same way, because some consumer, somewhere, is
already depending on the exact shape you shipped. The GNU coreutils flag
sprawl is the canonical example: it's not that the tools got sloppy, it's
that the "just pipe to a separate decompressor" purism was only ever
available *before* `tar zxvf` had a decade of scripts depending on it. The
old style of removing a feature to keep things minimal requires
convincing every consumer their existing usage will keep working — which
you usually can't.

This is a sharper, consequence-focused restatement of what
[[well-formed-interface]]'s "Trustworthy" facet asks for — that facet says
an interface should state its guarantees and hold to them; this principle
is the reason why: the guarantee isn't really optional or renegotiable
once someone else has built on it, no matter what the docs say.
[[semantic-versioning]] is the concrete mechanism for signaling *when*
you've crossed this line (a MINOR bump, in this repo's scheme, is exactly
"a consumer has to act because I changed a commitment").

The practical implication is about *timing*, not caution in general: the
cost of changing your mind about an interface's shape is lowest before
anyone outside your own change-set can see it, and rises sharply and
irreversibly the moment it does. Iterate freely and refactor without mercy
right up until that point — that's how the early Unix shell actually
arrived at its composition operators — then treat the release itself as
the expensive, hard-to-reverse step, not the code that led up to it.

**Why it matters:** treating "ship it" as a reversible checkpoint, the way
an internal refactor is, leads to publishing a shape you haven't actually
committed to yet — and then either breaking real consumers to fix it, or
being stuck maintaining a mistake indefinitely because fixing it costs
more than living with it.

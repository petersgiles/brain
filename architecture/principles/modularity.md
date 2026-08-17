---
name: modularity
type: principle
description: Build simple parts connected by clean interfaces, so most problems stay local and any one part can be replaced without breaking the whole.
---

Hold a system's global complexity down by building it out of simple parts
connected by well-defined interfaces. Debugging dominates development time;
a design where most problems are local, and where one part can be upgraded
without breaking the rest, is worth far more than a clever monolith. Unix
tradition calls this the Rule of Modularity.

This is the structural precondition for [[well-formed-interface]] — you
can't make a unit discoverable, addressable, or valuable on its own if it
isn't a genuinely separable part to begin with. It's also what
[[bounded-contexts]] does at the domain-modeling level: a boundary is only
worth drawing if the part behind it is actually simple in isolation.

**Why it matters:** the only way to write complex software that doesn't
collapse under its own weight is to keep most of that complexity local to
one small part at a time — a human brain can hold one simple part in mind
completely, but not a monolith where every piece touches every other piece.

**Caveat: "do one thing" is a means, not the goal.** Taken dogmatically, it
slides into a programmer-centric, feature-oriented mindset that fragments
tools past the point of usefulness — splitting a common task across three
invocations because each individual piece stayed "pure" is worse design
than one unit that directly handles the task people actually reach for
(`tar zxvf`, not a purist insistence on piping to a separate decompressor
every time). The point of modularity is that most problems stay local and
parts stay replaceable — not that every convenience a real user needs has
to be assembled by hand from smaller pieces every single time.

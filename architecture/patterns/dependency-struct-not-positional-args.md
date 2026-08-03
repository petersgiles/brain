---
name: dependency-struct-not-positional-args
type: pattern
description: Thread a growing set of collaborators through one named struct built at the composition root, not an ever-lengthening positional parameter list.
---

As the number of collaborators a unit needs grows, thread them through one
named struct built once at the [[composition-root]], rather than an
ever-lengthening positional parameter list. Extending what a unit depends
on then means adding a field to the struct's single definition site, not
editing every call site that constructs the unit.

This also makes dependencies self-documenting at the call site: a struct
literal with named fields reads as "here is exactly what this unit needs,"
where a long positional argument list reads as "match these up
correctly and hope."

Related: [[one-composition-root]], [[uniform-self-registering-interface]]
(which typically receives one of these structs as its `Register` argument).

---
name: one-composition-root
type: principle
description: Exactly one place in the system constructs concrete implementations and wires them to the abstractions that consume them.
---

Exactly one place in the system constructs concrete implementations and
wires them to the abstractions that use them. Everywhere else, a unit
receives its dependencies as explicit parameters — never a global, never a
service locator, never a package-level singleton reached for out of
convenience.

See [[composition-root]] (glossary) for the term itself, and
[[dependency-struct-not-positional-args]] for the concrete mechanism used to
keep the wiring manageable as the dependency count grows.

**Why it matters:** when construction is scattered, "what does this thing
actually depend on" stops being answerable by reading one file — you have
to trace every place it might get built. A single composition root makes
the whole dependency graph visible in one place, and makes every other unit
trivially testable in isolation, since nothing it depends on is implicit.

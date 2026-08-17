---
name: distrust-one-true-way
type: principle
description: No tool or design is optimised for every case its designer didn't anticipate — treat a rigid, closed "this is the one correct way" design as a warning sign, not a strength.
---

Distrust any claim of a single "one true way" to design or implement
something. Unix tradition calls this the Rule of Diversity. Even the best
tools are limited by their designers' imagination; nobody can optimise for
every use their software will eventually be put to, or anticipate every
case in advance. A design that's rigid and closed — that refuses to
compose with anything outside its own assumptions — is a form of
arrogance about how well its designer predicted the future, not a sign of
quality.

This is a caution about closedness and mistrust of forced uniformity, not
license to leave every option open — it pairs with, rather than
contradicts, [[minimal-necessary-abstraction]]: distrust the claim that
one approach is uniquely correct for every case, but don't pre-build
support for cases that don't exist yet just to avoid that claim. The
antidote to "one true way" is staying open and composable, not
speculative generality.

**Why it matters:** a system that assumes its own design is the final
answer tends to actively resist the use case that doesn't fit — the fix
gets fought as "not how this is supposed to be used" instead of being
absorbed, which is exactly backwards from what makes a design durable.

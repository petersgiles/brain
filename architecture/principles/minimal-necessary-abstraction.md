---
name: minimal-necessary-abstraction
type: principle
description: Build exactly what's asked. Don't generalise for a hypothetical future case — duplication beats the wrong abstraction until a third case proves it.
---

Build exactly what's asked. Don't add configurability, generality, or a new
layer of abstraction for a case that doesn't exist yet — three similar
lines of code beat a premature abstraction. Prefer duplication over the
wrong abstraction until a real third use case forces the issue.

See [[rule-of-three]] (glossary) for the specific heuristic this implies for
shared-library extraction, and [[extract-after-duplication-proves-itself]]
for how this plays out across whole codebases rather than just functions.

**Why it matters:** an abstraction built for a guessed-at future case is a
bet, and it's usually wrong about the shape of the real future need — you
end up paying for generality nothing uses, while the actual second use case
(when it arrives) doesn't fit the guessed shape anyway and has to be
half-forced in or half-worked around.

Unix tradition states this same idea as two of its own rules: the Rule of
Simplicity ("design for simplicity; add complexity only where you must")
and the Rule of Parsimony ("write a big program only when it is clear by
demonstration that nothing else will do"). Parsimony adds a specific
failure mode worth naming: large programs invite overinvestment in a
failed or suboptimal approach, because people are reluctant to throw away
the visible product of work already done. That's a second, separate cost
from the one above — not just "the abstraction was wrong," but "and now
it's expensive to admit that and back out."

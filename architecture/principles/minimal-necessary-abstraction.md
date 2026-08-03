---
name: minimal-necessary-abstraction
type: principle
description: Build exactly what's asked. Don't generalize for a hypothetical future case — duplication beats the wrong abstraction until a third case proves it.
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

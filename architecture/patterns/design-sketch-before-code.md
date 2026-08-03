---
name: design-sketch-before-code
type: pattern
description: A non-trivial architectural change gets a short living document first — problem, interface sketch, honest fit/strain section, explicit non-scope.
---

A non-trivial architectural change gets a short living document before
implementation:

1. The concrete problem, including the specific bug or friction that
   triggered it — not an abstract motivation.
2. A sketch of the actual interfaces/types being proposed, concrete enough
   to critique.
3. An honest **"where this fits vs. where it strains"** section, naming
   the extension points or cases the new pattern doesn't cleanly cover.
4. An explicit **"not sketched here"** boundary, so scope creep during
   implementation has something to check itself against.

This is what stops a good pattern from being force-fit onto a case it
doesn't suit — not every extension point is "just another registrable
unit" ([[self-registering-unit]] names this exact trap in its own
"where it strains" section). Writing the strain cases down *before* coding
is what makes them visible enough to route around, rather than discovered
mid-implementation when routing around them is expensive.

**Why it matters:** the discipline of writing sections 3 and 4 before code
exists is what catches "we're about to force a uniform interface onto a
non-uniform problem" while it's still cheap to change.

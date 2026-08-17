---
name: fold-knowledge-into-data
type: principle
description: Where you have a choice between complexity in a data structure and complexity in procedural logic, choose the data structure — data is far easier for a human to verify than control flow.
---

Where you have a choice between putting complexity in a data structure or
in procedural logic, choose the data structure. Unix tradition calls this
the Rule of Representation. Even a fairly complex data structure — a large
tree, a big lookup table — is easy for a human to model and reason about;
even simple procedural logic is comparatively hard to verify by inspection,
because you have to trace execution rather than just read a shape. Compare
an array-driven conversion table against the equivalent chain of
if/else branches: the data version is legible at a glance in a way the
logic version isn't.

In practice, this means actively looking for chances to shift complexity
from code to data as a design evolves, not just when starting from scratch.

This sits next to but is distinct from [[explicit-modeling]]: explicit
modeling is about not letting a truth be an *implicit* side effect of
which field happens to be populated; this rule is about *where* you put
complexity once a thing is already modeled explicitly — in the shape of
the data, rather than in branches that walk it.

**Why it matters:** program logic that encodes a lot of cases is hard to
verify — you have to trace every path. The equivalent knowledge folded
into a data structure can usually be read and checked directly, which
makes the logic that consumes it simpler and harder to get wrong.

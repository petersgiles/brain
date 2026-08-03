---
name: decide-once-at-the-authority
type: principle
description: Compute a presentation or business decision once, in the layer that owns the underlying rule, and hand it downstream ready-to-use.
---

A presentation, formatting, or business decision is computed once, in the
layer that owns the underlying data or rule, and handed downstream as
ready-to-use output — never re-derived independently by two or more
consumers.

Concretely: if a value needs a display label, a color, a visibility rule,
or a "should this even be shown" decision, that decision is made where the
underlying fact lives (typically a server/service layer), not recomputed in
every client that renders it. A thin rendering layer should be able to
render the decision without knowing the rule behind it.

**Why it matters:** duplicated decision logic is where silent drift between
copies comes from — one consumer's copy of the rule gets updated, another's
doesn't, and now two parts of the UI (or two services) disagree about the
same fact for no reason a bug report can easily name. This is
[[layered-authority]] applied specifically to *decisions*, not just data.

---
name: noun-verb-interaction-diagram
type: pattern
description: One page — entities as nodes, interactions as directed labeled verbs — scoped to core behavior, not the full possibility space.
---

Document "what can interact with what" as a single diagram: entities
(nouns) as nodes, interactions (verbs) as directed, labeled edges between
them. Group nodes by role with color, not by data schema. One page, meant
to be read at a glance, not a multi-page spec read once and shelved.

Two disciplines make this work, both easy to lose under pressure to be
complete:

1. **Core behavior only, not the possibility space.** The diagram charts
   what you've decided matters, not everything a determined designer could
   wire up. "Player picks up stick, waves it, jabs it in a socket" is
   possibility-space noise; "Player wields Weapon, Weapon defeats Monster"
   is core behavior. Naming that line explicitly, early, is what keeps the
   diagram legible — without it, the diagram grows to match the system's
   full combinatorial surface and stops being readable at a glance. This is
   [[minimal-necessary-abstraction]] applied to documentation itself: model
   what's decided, not what's merely possible.
2. **A shared, small verb vocabulary.** Verbs are the edge labels, so reuse
   ("provides," "defeats," "carries") does double duty — it keeps the
   diagram scannable and it's [[ubiquitous-language]] made visible: the
   same word means the same relationship everywhere it appears on the page.

The artifact is meant to be handled, not filed. Kept physically accessible
(laminated, on a whiteboard marker) so specific scenarios can be traced by
hand — "what happens if the player does X here" — before committing them
to flowcharts or code. That trace step is what surfaces gaps: an
interaction someone assumed existed but that has no edge on the page, or an
edge that implies a rule nobody had written down. This is the same
cheap-medium-before-expensive-medium move as
[[design-sketch-before-code]], one level more informal.

**Where this fits:** any domain with a bounded set of actor/entity
interactions worth agreeing on up front — game mechanics, but equally a
business-rules domain model (which roles can act on which resources, and
how). Read it as an actor-verb-entity capability map: a missing edge is a
question ("should Allies be able to do this to Monsters?"), not
necessarily a bug.

**Where this strains:** systems where the interesting complexity is in
*state* (thresholds, sequencing, quantities) rather than in *which actors
can act on which entities*. A noun-verb diagram shows that an interaction
exists, not the conditions under which it's valid — that still needs a
spec, flowchart, or rule table once the diagram has done its job of
scoping what's in play.

**Why it matters:** most documentation failure isn't missing detail, it's
unread detail — a multi-page doc that goes in a drawer. A one-page diagram
that gets drawn on during real scenario walkthroughs stays a living
reference instead, and the discipline of scoping it to core behavior is
what keeps it small enough to survive.

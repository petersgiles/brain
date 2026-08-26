---
name: accessibility-is-usability
type: principle
description: Accessibility isn't a separate compliance pass bolted on at the end — it's usability for a wider range of situations, and most of it is just good design applied consistently.
---

Treating accessibility as a distinct checklist run after a design is
"done" guarantees it always loses to schedule pressure, and frames it as
serving a separate group of users rather than as the same usability work
already being done for everyone else. Krug (*Don't Make Me Think*) makes
the case that most accessibility work — clear labels, sufficient
contrast, sensible reading order, controls reachable without a mouse —
is usability work that helps every user under some condition (bright
sunlight, a shaky trackpad, a noisy environment, a small screen), not a
feature that only matters for a minority.

The practical shift this implies: build the things accessibility asks
for as part of the same pass that builds the design at all — semantic
structure, real contrast, keyboard operability — rather than as a
retrofit applied to a visual design that was finished without them in
mind.

**Why it matters:** a retrofit is where accessibility work goes to be
deprioritized indefinitely; folding it into the same pass as the rest of
the design means it competes for the same attention as everything else
that has to work for the design to ship at all.

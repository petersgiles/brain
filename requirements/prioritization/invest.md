---
name: invest
type: framework
description: INVEST is a checklist for whether a single user story is well-formed — Independent, Negotiable, Valuable, Estimable, Small, Testable.
---

INVEST is a checklist applied to one user story at a time, not to a
backlog as a whole:

- **Independent** — can be built and delivered without waiting on
  another story.
- **Negotiable** — a starting point for a conversation, not a fixed
  contract handed down.
- **Valuable** — delivers something a user or stakeholder actually
  cares about, on its own.
- **Estimable** — the team knows enough about it to size the work.
- **Small** — fits comfortably inside one iteration.
- **Testable** — has a clear, checkable definition of done.

**Why it matters:** a story that fails one of these checks tends to fail
in the same predictable way later — a story that isn't Independent
blocks the burndown on sequencing; one that isn't Small either stalls
mid-iteration or gets silently descoped. Catching the failure at write
time is far cheaper than catching it mid-sprint.

**How to apply:** run new stories through INVEST before they go in the
backlog, not after they're picked up. A story that fails Small or
Independent should usually be split, not force-fit into one iteration.
Compare against [[moscow]], which sorts stories that already pass this
checklist — INVEST is about story *quality*, MoSCoW is about story
*priority*.

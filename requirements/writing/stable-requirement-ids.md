---
name: stable-requirement-ids
type: standard
description: Every requirement gets a permanent, dumb, sequential ID (context-prefix + number), assigned once and never reused, renumbered, or reused after removal.
---

Assign an ID to a requirement the moment it's created. Never change that
ID afterward, even if the requirement moves to a different section or
document.

Keep IDs dumb and sequential — `HOST-001`, `HOST-002` — one running
counter per prefix. Don't bake priority, phase, or category into the
number itself: those attributes change over time ([[requirement-tags]]
carries them instead), and a number that encodes one goes stale the
moment that attribute changes while the requirement itself hasn't.

Prefix the sequential number with a short context code identifying which
counter issued it — a bounded context, subsystem, or concern (`HOST-001`,
`LANG-014`, `SEC-042`). The prefix identifies a grouping, nothing more.

**Why it matters:** a requirement gets referenced by ID in conversation,
commits, and other documents. If the ID could change — renumbered when a
section reorders, or reused after the requirement is dropped — every
existing reference silently goes stale or starts pointing at the wrong
thing.

**How to apply:** when a requirement is superseded or removed, retire its
ID — record it as removed, don't reassign the number to something new.

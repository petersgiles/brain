---
name: requirement-tags
type: standard
description: Requirements carry a small set of concern tags in frontmatter, separate from their stable ID, so classification can change without ever touching identity.
---

Each requirement's frontmatter carries `tags:` — a short list of concern
labels (e.g. `domain`, `data`, `orchestration`, plus project-specific
module or subsystem tags). Tags classify what a requirement is about;
the [[stable-requirement-ids|ID]] only identifies which requirement it
is. Keep those two jobs separate — an ID never encodes a tag, and a tag
is free to change without ever touching the ID it's attached to.

Keep the tag vocabulary small and controlled per project. List the
allowed tags once, in the project's [[requirements-glossary|glossary]],
rather than letting free-text tags multiply into near-duplicates
("orchestration" in one file, "coordination" in another, for the same
concern).

**Why it matters:** classification is exactly the kind of attribute that
drifts as understanding of a system improves. Locking it into the ID
makes the ID wrong the moment the classification changes; keeping it in
frontmatter instead means reclassifying costs nothing and touches no
references.

**How to apply:** tag a requirement with the module/context that owns it
plus any cross-cutting concern it also touches (a Game Engine requirement
that calls into another module might carry both `game` and
`orchestration`). Define the controlled tag list before requirements
accumulate, not after.

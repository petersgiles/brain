---
name: one-requirement-per-file
type: standard
description: Frontmatter is a file-level construct, so a requirement carrying its own ID and tags means one requirement lives in one file, indexed from a lookup table.
---

Extends [[many-small-single-purpose-files]] to requirements specifically.
Because [[stable-requirement-ids|IDs]] and [[requirement-tags|tags]] live
in frontmatter, and frontmatter belongs to exactly one file, giving a
requirement its own frontmatter means it gets its own file — a file
holding several requirements has nowhere to put more than one ID.

Group a bounded context's requirement files under its own directory
(`requirements/host/HOST-001.md`, `HOST-002.md`, ...). Index every ID
from a single lookup table (ID, tags, priority, one-line text, link) — a
reader or an agent doesn't want to open twenty-four files to find
`GAME-003`.

**Why it matters:** the whole point of a stable ID ([[stable-requirement-ids]])
is being able to say "GAME-003" in conversation and have it resolve
instantly. That only works if there's exactly one file GAME-003 could be
in, and a table that resolves the ID to it without a search.

**How to apply:** when a requirements document already groups several
`shall` statements under one heading, split it: one file per statement,
frontmatter carrying its ID and tags, plus a lookup table that lists
every ID in the document.

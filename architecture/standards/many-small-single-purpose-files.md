---
name: many-small-single-purpose-files
type: standard
description: Prefer many small single-purpose files over one large file with sectioned comments, even within the same package or module.
---

Prefer many small, single-purpose files over one large file carved into
sections with comment banners — even within the same package/module. A
file should be findable and understandable by its name alone, without
needing to scroll to a section comment to know what part of it you're
reading.

Pairs with [[directory-layout-mirrors-layering]]: splitting by
responsibility at the file level and by layer at the directory level
together make navigation predictable purely from the file tree.

**Why it matters:** a large sectioned file hides its seams — refactoring or
reviewing a change to "just the X part" still means scrolling past
everything else in the file, and diffs against a huge file are noisier than
diffs against several small ones.

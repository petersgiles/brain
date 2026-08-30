---
name: requirements-glossary
type: standard
description: Pair a requirements document with a project-specific glossary of ubiquitous-language terms; bounded-context names and requirement tags are drawn from it, not invented ad hoc per file.
---

Extends [[ubiquitous-language]] to requirements documents specifically:
every bounded context name and every allowed [[requirement-tags|tag]] is
a term defined once, in a project glossary, not reinvented per file.

Use whichever granularity fits the project's current size — one file per
term (as `architecture/glossary/` does here, for heavy cross-linking) or
a single glossary file listing every term (fine for a smaller, single
project) — but pick one and keep the terms in it authoritative.

**Why it matters:** a tag or bounded-context name that isn't a defined
term drifts across documents — one file says "orchestration," another
says "coordination," for the same concern, and nothing catches the
mismatch.

**How to apply:** before adding a new tag or bounded-context name to a
requirements document, check the glossary for an existing term. Add the
term to the glossary the same time you first use it, never after.

---
name: directory-layout-mirrors-layering
type: standard
description: Raw external access, join/business logic, and thin entry points live in separate top-level directories, never mixed in the same file.
---

Raw external access (adapters), join/business logic (services), and thin
entry points (HTTP handlers, CLI commands) live in separate top-level
directories — never mixed together in the same file, regardless of how
small the feature is.

This is the filesystem-level expression of
[[name-by-architectural-role]] and [[layered-authority]]: if the directory
structure already tells you which layer owns which file, the role-based
naming and the layering principle reinforce each other instead of being two
separate things to remember.

**Why it matters:** when layering is only a naming convention and not also
a directory convention, it erodes gradually — a "quick" bit of business
logic ends up living in a handler file because nothing structural stopped
it.

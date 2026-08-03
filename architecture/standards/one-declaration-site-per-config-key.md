---
name: one-declaration-site-per-config-key
type: standard
description: A config key's existence, type, and default are decided in exactly one place; nothing else reads the raw environment source directly.
---

A config key's existence, type, and default are decided in exactly one
place — the [[config-loader-chain]]. Nothing else in the codebase reads the
raw environment/config accessor directly for a key the loader manages.

This means adding a new config value is always a one-line change to the
loader declaration, and there is never a question of "does this key have a
default somewhere else too" — there's exactly one place to check.

**Why it matters:** scattered raw reads of the same env var are how a key
ends up with two different defaults in two different places, silently,
each looking locally reasonable and only visibly wrong when compared
side by side.

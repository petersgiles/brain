---
name: config-loader-chain
type: pattern
description: One fluent builder collects every required and optional config value system-wide into a single chain, resolved once at startup.
---

A small fluent builder collects every required and optional config/env
value used anywhere in the system into one chain (e.g.
`Require(key)`, `Optional(key, default)`, groups of keys required only
together), resolved once at startup. A missing required value halts
startup with a clear message naming the exact key — never a confusing
runtime failure surfacing three calls deep from a `nil`/empty-string
default.

Nothing outside the loader calls the raw config/environment accessor
directly for a key the loader manages — see
[[one-declaration-site-per-config-key]].

**Why it matters:** this is the concrete mechanism that makes
[[fail-fast-no-fallbacks]] actually happen for configuration specifically,
instead of remaining an aspiration that individual `os.Getenv` call sites
each have to remember to honor.

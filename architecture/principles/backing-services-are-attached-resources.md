---
name: backing-services-are-attached-resources
type: principle
description: Every database, queue, cache, or third-party API is referenced only via config, never assumed to be a specific local instance — swapping one out is a config change, not a code change.
---

Treat every backing service — a database, a message queue, a cache, an
object store, a third-party API — as an attached resource, referenced
only through config (a URL, connection string, or credential set) that
[[config-loader-chain]] resolves once at boot. Nothing in the codebase
assumes a specific instance ("it's always Postgres on localhost:5432") or
reaches around the config layer to hardcode an address.

The seam where this becomes concrete is the Adapter role (see
[[name-by-architectural-role]]): an adapter's constructor takes the
resolved config values as arguments, never reads the environment itself,
and everything above it talks to the adapter's interface, not the
backing service's wire protocol.

**Why it matters:** when a backing service is truly just config, replacing
local Postgres with a managed instance, pointing staging at a different
Influx org, or running a second environment side by side is an operations
change, not a development task — and the codebase can't accumulate silent
assumptions about topology that only surface when that topology changes.

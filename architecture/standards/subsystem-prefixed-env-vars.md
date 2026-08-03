---
name: subsystem-prefixed-env-vars
type: standard
description: Env vars for one external dependency share one exact prefix and a plain, consistent attribute suffix — never two spellings of the same subsystem.
---

An environment variable name is `<SUBSYSTEM>_<ATTRIBUTE>`, in
`SCREAMING_SNAKE_CASE` — the near-universal POSIX/12-Factor convention
(see [12factor.net/config](https://12factor.net/config)): env vars are
case-sensitive, and all-caps signals "this is meant to be read by a
program," not a shell-internal or user variable.

Every variable for the same external dependency shares the exact same
`SUBSYSTEM` token, spelled identically, every time. `INFLUX_HOST`,
`INFLUX_TOKEN`, `INFLUX_ORGANISATION` — not `INFLUX_DB_HOST` next to
`INFLUXDB_TOKEN` next to `INFLUX_ORG`: three different compressions of
the same word (`INFLUX_DB` vs `INFLUXDB` vs bare `INFLUX`) is what makes
a config block look accidental instead of designed, and makes it
genuinely hard to grep or eyeball-scan for "every var this dependency
needs."

The `ATTRIBUTE` suffix names the thing plainly, at one consistent
abbreviation level across all of that subsystem's siblings —
`HOST`/`TOKEN`/`ORGANISATION`, not `HOST`/`TOKEN`/`ORG` (spelled out for
two, abbreviated for the third). Pick full words or pick abbreviations;
don't mix within one subsystem's key set.

Subsystem-first (not attribute-first) ordering — `INFLUX_HOST`, not
`HOST_INFLUX` — means every key for one dependency sorts and reads
together in a `.env` file, an `env | sort` listing, or a secrets
manager's key list, rather than being scattered alphabetically by
whichever attribute happened to come first.

**Why it matters:** naming drift like `INFLUX_DB_HOST` vs
`INFLUXDB_TOKEN` isn't just cosmetic — it means someone editing config
later can't safely guess a key's exact spelling from its siblings, and a
grep/search for "everything Influx-related" silently misses whichever
variant they didn't think to check.

Related: [[one-declaration-site-per-config-key]] covers *where* a key is
declared; this covers what the key is *called*. See also
[[config-loader-chain]].

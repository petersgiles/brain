---
name: semantic-versioning
type: standard
description: MAJOR.MINOR.PATCH — MAJOR for anything that requires operator action to keep working, MINOR for backward-compatible additions, PATCH for backward-compatible fixes.
---

Every release is tagged `MAJOR.MINOR.PATCH`:

- **MAJOR** increments for a breaking change — anything that requires
  action (by an operator, a deployment, or a caller) before the system
  keeps working the same way it did. For a deployed application, not just
  a published library, that includes: a renamed or newly-required config
  key, a config file format change, a database migration that isn't
  backward compatible, a removed or reshaped API endpoint an existing
  caller depends on, a changed wire contract. "The public function
  signature changed" is the library-centric definition; it's too narrow
  for anything with no external consumers of its source-level API but
  real consumers of its config, its endpoints, or its data.
- **MINOR** increments for a backward-compatible addition — a new
  feature, a new optional config key with a sensible default, a new
  endpoint — that doesn't require anyone to change anything to keep
  working.
- **PATCH** increments for a backward-compatible fix — a bug fix, a
  visual or copy change, a refactor with no observable behavior change.

Below `1.0.0`, none of this is guaranteed yet — a pre-1.0 version signals
"the interface can still change without notice," which is why crossing
`1.0.0` itself is a meaningful, deliberate act, not just another bump.

**Why it matters:** a version number is a promise a consumer relies on
without reading the changelog — seeing only the PATCH digit change is
what lets someone deploy an update without re-checking their own config
or integration. Under-counting a breaking change as a PATCH (or a MINOR)
breaks that promise silently, and the first sign of it is usually a
production incident, not a code review comment.

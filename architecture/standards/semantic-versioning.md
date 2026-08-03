---
name: semantic-versioning
type: standard
description: MAJOR.MINOR.PATCH — MAJOR is a product-launch decision, not a technical one; MINOR is for changes that require an operator to act; PATCH is everything else, including new backward-compatible features.
---

Every release is tagged `MAJOR.MINOR.PATCH`. For a continuously-deployed
application with no external consumers reading a changelog to decide
whether it's safe to upgrade — as opposed to a published library or a
versioned public API — the practical line sits differently than textbook
semver:

- **MINOR** increments for anything that requires an operator to do
  something before the system keeps working the same way it did: a
  renamed or newly-required config key, a config file format change, a
  non-backward-compatible migration, a removed or reshaped endpoint an
  existing caller depends on. This is what a library would call a
  breaking (MAJOR) change — for an app whose only "consumers" are its own
  deployments, requiring a config/deploy-time action is a MINOR-level
  event, not a MAJOR one.
- **PATCH** increments for everything backward-compatible: bug fixes,
  visual/copy changes, refactors with no observable behavior change —
  *and* new features, toggles, or new optional config with a safe
  default. A new capability that nobody has to do anything to keep
  benefiting from their existing setup doesn't earn a MINOR bump just for
  being new; the deciding question is "does an operator have to act,"
  not "is this new."
- **MAJOR** is a product decision, not a technical one — it changes when
  there's an official launch of a new complete version of the product,
  full stop. No amount of accumulated features, breaking config changes,
  or internal rework bumps it on its own; only the deliberate call that
  "this is the next product release" does. Crossing `1.0.0` is the same
  kind of act: the first official launch, not a technical milestone like
  "feature-complete" or "stable API."

If a project *does* have external consumers who read this version number
to decide whether to upgrade (a published library, a public API), fall
back to textbook semver instead: MAJOR for breaking, MINOR for
backward-compatible additions, PATCH for backward-compatible fixes. The
distinction above only applies once there's no such audience.

**Why it matters:** a version number is a promise a consumer relies on
without reading the full changelog. For an internal app, the promise
that matters in practice is narrower — "did the PATCH-to-PATCH bump
require me to touch config" — and bumping MINOR for routine new features
dilutes that signal, making every release look like it might need
attention when almost none of them do.

---
name: restart-before-rebuild
type: pattern
description: A dev container's default refresh is a plain restart; a full image rebuild is reserved for an actual dependency-manifest change, not routine iteration.
---

A dev environment should be structured so the common case — "I changed
some source, let me see it" — never requires rebuilding a container image.
Bind-mount the app's own repo and any sibling repos it depends on (a
language workspace mechanism like Go's `go.work`, or an equivalent) so
in-process hot-reload picks up source changes live. Compile assets (CSS,
etc.) on the host straight into a bind-mounted output path the container
serves directly, rather than baking that compile step into the image.
What's left needing an actual image rebuild shrinks to one thing: a
dependency manifest changed (a new package version, a new system
package) — and that's the only time `--build` (or equivalent) is
warranted.

Restarting is cheap and safe to reach for by default — see
[[disposable-processes]]. Rebuilding is not: it re-runs every fetch/install
step, including ones gated behind registry or VCS auth that may fail for
reasons that have nothing to do with the change being tested, and a
compose-style `up --build` typically tears down the running container
*before* attempting the rebuild — so a failed rebuild can leave nothing
running at all, when a restart would have left the working version alone.

**Why it matters:** treating "test this" as "rebuild the image" turns every
iteration into a slower, riskier operation than it needs to be, and
couples routine verification to infrastructure (registry credentials,
network access) that routine verification shouldn't depend on. When in
doubt about which one a change needs, restart first — a rebuild is
something to reach for deliberately, not by default. See
[[verify-against-a-running-instance]] for the broader principle this
serves.

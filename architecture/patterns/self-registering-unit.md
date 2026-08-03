---
name: self-registering-unit
type: pattern
description: A feature unit implements a small interface and registers itself into a shared registry, so the composition root reduces to one generic loop.
---

A feature unit — a page, a plugin, a data source — implements a small,
shared interface and registers itself into a common registry, either at
load time (`init()`-style self-registration) or via one explicit call at
the point it's constructed. The composition root then shrinks to a single
generic loop over "whatever is registered," instead of a hand-maintained
list that grows one line per feature, in a specific order, and silently
does nothing if a step is missed (wrong flag, missing entry, 404).

In a statically compiled language there's no free lunch here — one
reference/import line per unit is the honest, unavoidable floor (see
[[boring-composition-over-dynamic-loading]]). That's fine: that one line
*is* the record of intentional inclusion, not friction worth engineering
away.

**Where it fits:** independent, self-contained units that never need to be
merged with each other — a set of pages/routes, a set of format decoders, a
set of metric collectors.

**Where it strains:** an extension point that needs a hook *into* the
frame rather than a slot *on* it (an error-page fallback, a route a
dependency already owns) doesn't fit the same `Register()` shape — don't
force it through the identical interface just for uniformity; give it its
own registration method instead. See [[design-sketch-before-code]].

Related: [[registry-and-compose]] (the many-to-one variant of this same
idea), [[uniform-self-registering-interface]] (the naming/shape standard
this implies), [[composition-root]].

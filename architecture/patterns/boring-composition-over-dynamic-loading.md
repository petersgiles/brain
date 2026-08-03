---
name: boring-composition-over-dynamic-loading
type: pattern
description: In ecosystems without cheap safe dynamic loading, don't reach for a plugin/reflection mechanism just to avoid one static reference line.
---

In ecosystems without cheap, safe dynamic loading (most compiled
languages), don't reach for a plugin or reflection-based loading mechanism
to avoid writing one static reference/import line per unit. That trade
swaps small, visible, compile-time-checked friction today for a "works in
dev, breaks on the build server" failure mode later — dynamic plugin
loading typically demands an exact toolchain/dependency match between host
and plugin that's brittle across environments and platforms.

Standard practice in exactly this situation — driver registries, format
decoders, metrics collectors — is self-registration behind a single static
import, not runtime plugin loading. See [[self-registering-unit]] for the
mechanism this justifies.

**Why it matters:** the one-line-per-unit floor isn't a limitation to
engineer around — it's the cheapest possible price for "this binary
definitely, verifiably includes this unit," checked by the compiler instead
of discovered at runtime.

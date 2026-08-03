---
name: name-by-architectural-role
type: standard
description: A unit's name suffix says what it does in the layering, not what data it touches — Adapter, Service, Controller, View/DTO, Source, Guard, Loader.
---

Name a unit by its architectural role, not by the data it happens to touch:

- **Adapter** — raw I/O against one external system; no business logic.
- **Service** — business/join logic across one or more adapters.
- **Controller/Handler** — thin; parses a request, delegates to a service,
  formats a response; owns no logic of its own.
- **View/DTO** — a typed, documented, stable wire-boundary shape.
- **Source** — a registrable contributor into a composed/merged record
  (see [[registry-and-compose]]).
- **Guard** — a single-purpose trust/auth check on a route or action
  (see [[guards-named-for-the-check]]).
- **Loader/Builder** — something that resolves configuration once, up front
  (see [[config-loader-chain]]).

**Why it matters:** a consistent role vocabulary means a reader can predict
a file's responsibility from its name alone, before opening it — and it
makes violations visible ("why does this Adapter contain business logic")
instead of invisible.

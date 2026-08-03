---
name: guards-named-for-the-check
type: standard
description: Name a guard/middleware for the condition it checks, not for who's expected to use it.
---

Name a guard or middleware for the specific condition it checks, not for
who's expected to use it — "same-process caller" beats "internal guard";
"cloud-scoped peer token" beats "mesh guard" if that's genuinely all it
checks. The name should make the trust boundary legible from the name
alone, without reading the implementation.

This matters most exactly where [[layered-trust-guards]] warns about
casual reuse: a name like "internal guard" invites someone to slap it on a
new route because it *sounds* like it means "trusted," even when what it
actually checks is much narrower (e.g., only same-container loopback, not
"any code we wrote").

**Why it matters:** a guard's name is often the only thing a future
reviewer checks before approving a new route that uses it — a vague name
makes that review shallow by construction.

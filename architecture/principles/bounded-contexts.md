---
name: bounded-contexts
type: principle
description: A concept's meaning is only ever authoritative within an explicit boundary; the same term meaning different things in different contexts is expected, not a naming collision to resolve.
---

A domain concept doesn't have one universal definition across an entire
system — it has one authoritative definition within an explicit boundary
(a bounded context), and different boundaries are free to define the same
term differently. "Customer" in a billing context (has an invoice history,
a payment method) is not the same shape as "Customer" in a support context
(has a ticket history, a preferred contact channel) — modeling them as one
shared entity forces an artificial merge that satisfies neither context
well.

Each bounded context gets its own model, and the boundary between two
contexts is where translation happens explicitly — a mapping, an adapter,
an API contract — never by silently assuming both sides mean the same
thing by the same word.

This is the domain-modeling analog of [[layered-authority]]: instead of
one layer being authoritative for a value, one context is authoritative
for what a term *means*, and everything else either lives inside that
context or explicitly translates at its edge. See also
[[ubiquitous-language]] for what happens inside one context's boundary.

**Why it matters:** forcing one universal model of every concept across
an entire system is what produces the giant, everything-entity classes
that nothing actually fits cleanly — every team's edge cases pile onto
the same shared definition until it satisfies no one. Explicit boundaries
let each context's model stay simple and exactly right for its own use,
at the cost of an explicit — not implicit — translation wherever contexts
meet.

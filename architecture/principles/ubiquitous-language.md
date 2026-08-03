---
name: ubiquitous-language
type: principle
description: Within a bounded context, code, conversation, and documentation use exactly the same vocabulary as domain experts — no translation layer between what the business calls it and what the code calls it.
---

Within one [[bounded-contexts|bounded context]], the vocabulary domain
experts use in conversation is the exact vocabulary that appears in the
code — class names, method names, field names — not a technical synonym
translated from the domain term. If domain experts talk about a
"consignment," the code has a `Consignment`, not a `Shipment` or a
`DeliveryOrder` that a developer privately maps back to "consignment"
every time they read it.

This runs in both directions: when the domain's language changes (a new
distinction, a renamed concept), the code changes with it — and when the
code reveals a distinction conversation had been glossing over, the
domain language absorbs that new term too.

**Why it matters:** a translation layer between "what the business says"
and "what the code says" is a permanent tax — every discussion needs
someone to mentally convert terms, and every mismatch is a place a subtle
misunderstanding can hide, undetected, because both sides think they're
talking about the same thing. A shared vocabulary lets a domain expert
read a method signature, or a developer sit in on a domain conversation,
without translation loss either way.

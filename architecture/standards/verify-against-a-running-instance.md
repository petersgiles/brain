---
name: verify-against-a-running-instance
type: standard
description: Verify changes against a real running instance of the system, in the closest available analog to production — not ad hoc local execution.
---

Verify changes against a real running instance of the system — the closest
available analog to production (containers, a staged environment) — rather
than ad hoc local execution that skips the packaging/runtime differences
production actually has. Don't leave temporary verification instrumentation
(test binaries copied into a running environment, debug endpoints, etc.)
embedded in the shipped system afterward.

**Why it matters:** "it works when I run it directly" and "it works in the
actual runtime environment" are different claims, and the gap between them
(missing env vars, different filesystem layout, different network
boundaries) is exactly where deploy-time surprises come from.

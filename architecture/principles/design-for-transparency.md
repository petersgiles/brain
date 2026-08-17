---
name: design-for-transparency
type: principle
description: Build in visibility into internal state from the start, so the system can demonstrate its own correctness and be inspected without special tooling bolted on afterward.
---

Design for *transparency* and *discoverability* from the beginning, rather
than treating debugging support as an afterthought. Unix tradition calls
this the Rule of Transparency. A system is transparent when you can look at
it and immediately understand what it's doing and how; it's discoverable
when it exposes its own internal state well enough to be monitored, not
just inferred from outside behavior.

This has to be designed in, not bolted on: it implies using input and
output formats simple enough that the relationship between valid input and
correct output is easy to check by inspection, and interfaces simple
enough that other programs — test harnesses, monitoring scripts, debugging
tools — can drive and observe the system without special-casing it.

[[logs-are-event-streams]] is the specific mechanism this implies for one
channel — a plain, structured event stream is the cheapest way to make
runtime behavior inspectable. [[robustness-through-simplicity]] is the
payoff transparency buys once paired with [[modularity]].

**Why it matters:** debugging typically consumes three-quarters or more of
development time. Work spent early making a system transparent is repaid
every time afterward that someone — including its own author — has to
figure out what it's actually doing.

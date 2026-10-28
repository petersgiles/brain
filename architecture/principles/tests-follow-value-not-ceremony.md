---
name: tests-follow-value-not-ceremony
type: principle
description: Spend test effort where it buys the most (the testing trophy: static checks, then validation and unit tests of our own data and logic, then integration of composed parts), test the outcome of an intent rather than how it was reached, and never test the engine or a third-party asset.
---

A test earns its place by catching a mistake in something we wrote, cheaply,
for as long as that thing lives. Count the cost too: every test is code to
keep, and most of a young project's code is thrown away before it ships.

Weight the effort like a trophy (Kent C. Dodds), widest in the middle:

1. **Static checks** (lint, types, validators) — cheapest, and they hold
   the architecture rules ([[tooling-is-the-ledger]]). Anything checkable
   goes here first.
2. **Unit tests of our own data and logic** — does the loader load the data
   as expected, does a decision function decide. Plain inputs, plain
   outputs, no timing.
3. **Integration tests of composed parts** — the main value when the system
   is built from composable parts: the parts work *together*. Shape of the
   test: **intent → action → outcome**. Send the intent or command in,
   check the events or the final state out. Do not assert the route taken
   (which clip name played, which signal fired first, how many frames).
4. **Functional testing by a person** — clicking around finds what no
   script will. Say in the suite what it leaves to them (a manual list),
   so a green run never implies coverage it lacks.

**Do not test:**

- The engine or a library (does an animation node play, does a tween
  move) or a third-party asset (how many frames a clip has). Assume what
  ships with the game works.
- An implementation that is likely to be rewritten. A test that pins the
  current internals costs more to keep than the code it covers.
- With a state machine, the testable claims are about *our* wiring: on this
  event the state moves this way, the clip it names runs, the callback is
  heard.

**"Prove a new test can fail"** — break the code on purpose once and watch
the test go red. The point is not ceremony per test; it is to catch a test
that passes without exercising anything (an agent once wrote tests that
passed without touching the code, to keep moving). Apply it to the few
tests that matter, not as a licence to write one per change.

**Why it matters:** a green suite feels like proof of care, and that makes
it easy to grow a suite larger than the code, slow to run and costly to
change, while the faults that matter are found by running the thing. Weigh
each test by what it protects and for how long.

Related: [[prototype-before-polishing]] (code is a draft), [[boundary-validation]]
(validate data where it is loaded), [[minimal-necessary-abstraction]],
[[verify-against-a-running-instance]].

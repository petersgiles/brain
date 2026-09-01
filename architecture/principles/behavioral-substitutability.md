---
name: behavioral-substitutability
type: principle
description: Any implementation of a shared contract must be swappable for another without surprising the caller — matching the contract's behaviour, not just its signature.
---

Any concrete implementation of a shared interface, protocol, or contract
must be swappable for another implementation of the same contract without
breaking the caller's expectations. Matching the method signatures isn't
enough — the caller relies on the contract's *behaviour*: its preconditions,
postconditions, and invariants. An implementation that satisfies the shape
but violates the behaviour (throws where the contract promises a value,
narrows what it accepts, widens what it returns, silently no-ops where the
contract promises an effect) is not actually substitutable, even though it
type-checks.

This isn't specific to class inheritance — it applies wherever multiple
concrete things satisfy one abstraction: Go interfaces, Python structural
typing/protocols, a set of Terraform providers behind one resource type, or
several adapters registered against the same port. The mechanism differs by
language; the obligation doesn't.

See [[one-composition-root]] and
[[backing-services-are-attached-resources]] for where this obligation gets
exercised in practice — swapping a concrete implementation at the root, or
a backing service via config, only stays safe if every candidate actually
honours the contract's behaviour, not just its signature.

**Why it matters:** a violation here doesn't fail at compile time — it
fails at runtime, in whichever caller happened to depend on the behaviour
the substitute broke, often nowhere near the substitution itself. The bug
report lands far from its cause.

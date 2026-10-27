---
name: tooling-is-the-ledger
type: principle
description: Code is a draft, not a gold standard — make it work, then improve it, moving every checkable rule into tooling that runs after each change; the tool's output is the ledger of how well the code follows the architecture.
---

Code is a draft, not a gold standard. First make it work. Then improve it:
find the patterns, build the domains, correct who owns what, and push
catches and branching logic out of production code and into design-time
tooling, so what ships is lean and built for its purpose. The system stays a
few edits away from running at all times; each increment is validated by
tooling that measures what is still wrong.

- **Anything checkable goes in tooling** — a lint, a validator, a test —
  that runs after every change. Its output is the **ledger**: a running,
  honest record of how well the code follows the architectural principles.
- **The tool also changes how we think.** A rule that is only written down
  gets argued with; a rule that is measured gets met.
- **Existing code is evidence, not authority.** A violation found in the
  codebase is a thing to fix, not a precedent to match. "It is already like
  that" is never a reason.
- **Fix trivial violations; do not work around them.** When asked to observe
  a rule, make the fix, even when annotating or reshaping the code would turn
  the tool green sooner. An exception is for a deliberate case only, and it
  carries its reason in the code beside it (for example
  `lint:allow-default <why>`), so the ledger records every exception too.
- **Prefer the check at design time.** Validate data when it is loaded and
  stop loudly ([[fail-fast-no-fallbacks]], [[boundary-validation]]) instead
  of guarding for bad data at run time.

Related: [[prototype-before-polishing]] (work first, improve second),
[[decide-once-at-the-authority]] (the usual fix a tool points to),
[[extract-after-duplication-proves-itself]], [[design-for-transparency]],
and [[layered-secret-scanning]] (baseline what exists, fail only on what is
new).

**Why it matters:** an agent or a person who treats the existing code as the
standard freezes its flaws in place, and one who works around a rule hides
the very signal the tool exists to give. A ledger that cannot be gamed lets
the code get better in small steps without anyone having to remember the
rules.

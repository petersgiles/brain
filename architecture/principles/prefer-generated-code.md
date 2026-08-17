---
name: prefer-generated-code
type: principle
description: Where hand-writing code is repetitive and error-prone, write a generator instead — a program that writes correct code reliably beats a human hand-writing the same shape repeatedly.
---

Avoid hand-hacking repetitive code; where the pattern is regular enough,
write a program to write the program. Unix tradition calls this the Rule
of Generation. Humans are bad at sweating repetitive detail — the simpler
and more abstracted a specification can be, the more likely a human
designer got it right, and generated code at any level is almost always
more reliable than the equivalent hand-written code, for the same reason a
compiler's output is more reliable than hand-written assembly.

This pays off specifically when the specification language for the
generator is genuinely simpler than the code it produces, and the
generated output doesn't need hand-editing afterward — parser/lexer
generators and typed clients generated from a schema are the classic
cases. It doesn't pay off for one-off logic with no repeating shape; that's
just an abstraction looking for an excuse, see
[[minimal-necessary-abstraction]].

**Why it matters:** hand-written repetition is a rich source of small,
inconsistent errors — the tenth copy of a pattern drifts slightly from the
first. A generator produces the same correct shape every time, and a bug
found in it is fixed everywhere at once instead of needing to be found and
fixed in every copy.

---
name: clarity-over-cleverness
type: principle
description: Write code as if its most important reader is the human who maintains it later, not the computer that executes it now — a small performance win isn't worth a large increase in obscurity.
---

Write programs as if the most important communication they do is not to the
computer that executes them but to the human beings who will read and
maintain the source later — including yourself, months on. Unix tradition
calls this the Rule of Clarity.

Buying a small performance gain with a large increase in complexity or
obscurity is a bad trade: complex code is more likely to harbor bugs, and
harder for the next person to change safely even when it's correct. Code
that's graceful and clear is both less likely to break and more likely to
be instantly understood by whoever touches it next.

A practical trigger: if you find yourself deciphering the same piece of
subtle code a second time — because the first pass was too long ago to
remember — that's the signal to simplify or comment it, before a third
reader (possibly future-you) pays the same cost again.

**Why it matters:** debugging and maintenance consume far more time than
initial writing does. Optimizing for the writer's cleverness in the moment
trades a tiny, one-time win for a recurring cost paid by every future
reader.

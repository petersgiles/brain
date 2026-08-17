---
name: least-surprise
type: principle
description: An interface should do the thing its audience already expects from prior experience — the easiest interfaces to use are the ones that demand the least new learning.
---

In interface design, always do the least surprising thing — also known as
the Principle of Least Astonishment. Unix tradition calls it the Rule of
Least Surprise. The easiest interfaces to use are the ones that connect to
a user's pre-existing knowledge instead of demanding new learning: if
you're building a calculator, `+` means addition, full stop.

Two things this implies in practice:

- **Know your audience.** What counts as "least surprising" differs
  between end users, other programmers, and operators — model an interface
  on the interfaces of functionally similar tools that *audience* already
  knows, not on what's familiar to you as the builder.
- **Distinctly different beats almost the same.** Something superficially
  similar but subtly different is more dangerous than something plainly
  different, because the surface familiarity invites the wrong assumptions
  to carry over. When you can't match an existing convention exactly,
  it's often safer to look nothing like it than to look almost like it.

This is a sharper, audience-facing lens on the "Understandable" facet of
[[well-formed-interface]] — that facet asks whether a thing documents
itself; this rule asks whether it behaves the way its audience would
already guess, documentation aside.

**Why it matters:** a surprising interface forces every user to build a new
mental model from scratch and re-verify their assumptions on every use.
Conforming to existing expectations means that learning cost gets paid
once, elsewhere, by whatever established the convention.

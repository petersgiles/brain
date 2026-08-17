---
name: robustness-through-simplicity
type: principle
description: A system is robust when its internals are simple and transparent enough for a human to reason about all the cases at once — robustness isn't a separate thing you add, it falls out of the other two.
---

Software is robust when it performs well under conditions that stress the
designer's assumptions, not just under the conditions it was explicitly
built for. Unix tradition calls this the Rule of Robustness, and states it
as a direct consequence of two other rules: robustness is the child of
[[design-for-transparency]] and simplicity ([[minimal-necessary-abstraction]]).

Most software is fragile because it's too complicated for a human brain to
hold in mind all at once — and when you can't reason correctly about a
program's internals, you can't be confident it's correct, and you can't
reliably fix it when it breaks. The fix isn't a separate "make it robust"
step; it's making the internals easy enough to reason about that edge
cases stop hiding. Avoiding special cases in the code matters here more
than it looks: bugs concentrate in the code that handles special cases,
and especially in the interactions between several special cases at once.

**Why it matters:** treating robustness as a bolt-on (more error handling,
more defensive checks) without addressing the underlying complexity just
adds more code for bugs to hide in. Real robustness comes from a system
simple enough that a human can actually see every case, not from armoring
a system too complex to see through.

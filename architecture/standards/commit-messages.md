---
name: commit-messages
type: standard
description: Subject is a short, imperative statement of what changed; a body — only when it earns one — carries the why a diff can't show, never a line-by-line narration of the diff itself.
---

- **Subject line**: imperative mood, concise, states what changed at the
  level a `git log --oneline` reader needs — no trailing period, no
  filler ("various fixes", "updates").
- **Body is optional.** Add one only when there's a *why* the diff itself
  can't carry: the motivation, an alternative that was rejected and why,
  the incident or decision that prompted this, cross-references to
  related work. Skip it when the subject already says everything worth
  saying — most single-idea commits don't need one.
- **Never narrate the diff line by line.** "Changed `X` to add parameter
  `Y`" adds nothing over `git show` — that's the same "restating what's
  already visible" failure [[commenting-code]] rules out for comments,
  aimed at the diff instead of the code.
- This is where [[commenting-code]]'s banned narration is *supposed* to
  live instead: "fixed to handle the null case," "added for the export
  flow," "changed per issue #123" belong in a commit body, not a comment
  next to the code.

**Why it matters:** a diff is frozen at its revision — a body explaining
*why* next to a diff that already shows *what* stays true forever. The
same narration placed as a comment in the source doesn't: the code moves
on, the comment doesn't, and it goes stale the moment the next change
lands.

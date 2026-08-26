---
name: commenting-code
type: standard
description: A short one-liner above non-trivial code is fine, but a comment states a timeless fact about the code — never a restatement of the next line, and never a narration of the change that produced it.
---

A comment is not banned by default here — a short one-liner above a
non-trivial function or block is fine even when nothing about it is a
hidden trap. What's not fine is *what* a comment is allowed to say:

- **Never restate the code in prose.** If a comment could be produced by
  translating the next line word-for-word into English — `// increment
  count` above `count += 1` — it adds nothing a reader didn't already
  have. Delete it.
- **Never narrate the change, the task, or the diff.** A comment
  describes the code as it stands today, not the history that produced
  it. No `// fixed to handle the null case`, `// added for the export
  flow`, `// changed per issue #123`, `// removed the old validation
  here`. That belongs in the commit message ([[commit-messages]]). The
  moment the next change
  lands, "the fix" and "the old way" stop meaning anything to a reader
  seeing the code cold — the comment has already gone stale, on day one.
- **Prefer why over what.** The comments worth keeping name a hidden
  constraint, a non-obvious invariant, or the reason a more obvious
  alternative doesn't work — the kind of thing [[clarity-over-cleverness]]
  says is worth a second look before a third reader pays to re-derive it.
- **One or two sentences.** If it needs a paragraph, that's a sign the
  code wants a better name or a smaller function, not more prose bolted
  onto it.

This is the same instinct as [[purposeful-silence]] applied to source
instead of output: a comment is also something competing for the reader's
attention, and it should only claim that attention when it's telling the
reader something the code itself can't.

**Why it matters:** a comment that restates the code or narrates a
changeset rots immediately, because the code keeps moving and the comment
doesn't — and a reader trusts the comment's story about what happened over
what the code in front of them actually does.

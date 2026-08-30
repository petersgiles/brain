---
name: specs-describe-the-system-not-their-authorship
type: principle
description: A specification states the current truth about the system; it never narrates how it was drafted, revised, or agreed on.
---

Agents writing documentation have a strong tendency to narrate the process
of creating the document as part of the document itself — "this section
was added after further discussion," "originally we considered X but
changed to Y," "per the user's clarification, the following was updated."
That narration does not belong in a specification.

A spec's job is to describe the system — as built or as required — to a
reader who wasn't in the room when it was written. Process commentary
answers a question nobody reading the spec is asking. It also decays
immediately: the next revision makes "originally we considered X" both
irrelevant and confusing, since X is no longer under consideration by
anyone.

**Why it matters:** a reader (human or agent) needs to trust that
everything in the document is a current, settled statement about the
system. Mixing in commentary about the document's own history forces the
reader to work out which sentences are the spec and which are meta-noise
about writing the spec — the exact failure [[purposeful-silence]] warns
against, applied to documentation instead of program output.

**How to apply:** if something changed, update the spec to state the
current truth — don't describe the change in prose alongside it. History
of *how a requirement came to be* belongs in a commit message, PR
description, or changelog, never inline in the requirement itself.

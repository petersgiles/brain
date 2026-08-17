---
name: purposeful-silence
type: principle
description: When a program has nothing surprising to report, it should say nothing — treat the reader's attention as a limited resource, only claimed when there's something they actually need to know.
---

When a program has nothing interesting or surprising to say, it should say
nothing. Unix tradition calls this the Rule of Silence. A well-behaved
program does its job with a minimum of fuss, and treats the reader's
attention as a limited, valuable resource — only claimed when there's
something that actually needs it.

This matters for both machine and human readers. When one program's output
becomes another's input ([[well-formed-interface]]'s "interoperable"
facet), the needed bits have to be easy to pick out — routine "still
working" noise makes that harder, not easier. For a human, if everything
displayed is important, then important information is trivially easy to
find; mix it in with routine status chatter and it isn't.

This governs *volume and relevance*, not durability of output —
[[logs-are-event-streams]] is the mechanism for the events that *are*
worth emitting; this rule is what keeps deciding an event is worth
emitting in the first place.

**Why it matters:** verbose-by-default output trains its own readers to
stop reading closely, because most of what scrolls past is noise. That's
exactly the moment a real, surprising failure is most likely to be
missed.

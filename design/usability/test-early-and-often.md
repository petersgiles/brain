---
name: test-early-and-often
type: standard
description: A little usability testing done constantly beats a large study done once — one participant this week outperforms a "properly representative" panel scheduled for next quarter.
---

Krug (*Don't Make Me Think*) argues for testing with about three people
a month, on whatever's currently in progress, rather than saving up for
one large, methodologically rigorous round. Almost any real person
surfaces most of the serious problems — recruiting a "perfectly
representative" panel matters far less than getting *someone* to try the
thing before it ships, since the biggest problems tend to trip up nearly
everyone, not just the target persona.

The failure mode this guards against isn't skipping testing outright —
it's treating testing as a big, expensive, occasional event, which makes
it easy to defer indefinitely and means feedback always arrives after
the design is already committed. Small and frequent keeps testing cheap
enough that skipping it stops being the path of least resistance.

**Why it matters:** a problem caught while a design is still cheap to
change costs a redraw; the same problem caught after ship costs a
migration, a support queue, or a silently-abandoned feature — testing
late doesn't just delay the finding, it multiplies its cost.

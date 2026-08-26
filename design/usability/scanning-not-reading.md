---
name: scanning-not-reading
type: principle
description: Design for a user scanning for the one thing they came for, not one reading every word — most text on a screen goes unread by design, not by user failure.
---

People don't read screens, they scan them — hunting for a word, a
shape, or a link that looks like the thing they came for, and clicking
the first reasonable match rather than comparing every option first
(Krug, *Don't Make Me Think*, calls the second habit "satisficing").
Once something looks like it's working, most users keep going without
understanding why it worked — "muddling through" rather than building an
accurate model of the system.

None of this is a user failing to pay attention. It's the default mode
for reading anything on a screen, under time pressure, among other tabs.
Designing against it — assuming careful, linear reading — produces
interfaces that work in a demo and fail in actual use.

Design for the scanning user: a clear visual hierarchy so headings and
labels are the things a scanning eye catches first; short chunks over
long paragraphs; the important word first in a heading or link, not
buried in the middle; conventional placement for conventional things
(nav at the top, search where search always is) so recognition replaces
reading entirely.

**Why it matters:** copy and layout aimed at a careful, complete reader
is invisible to a scanning one — the content might as well not be there
if it doesn't survive a half-second glance.

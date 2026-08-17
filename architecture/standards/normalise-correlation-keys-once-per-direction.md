---
name: normalise-correlation-keys-once-per-direction
type: standard
description: Pick one place a shared ID gets normalised to its internal canonical form, and one place it gets re-decorated for external display.
---

When an identifier or correlation key (an ID, a serial number, a slug) is
used to join data from otherwise-independent sources, pick exactly one
place it gets normalised to its canonical internal form on the way in, and
exactly one place it gets re-decorated into its external/display form on
the way out. Don't repeat either transform ad hoc wherever the key happens
to be used — every additional place that reimplements "strip this prefix"
or "reattach this prefix" is a place that can drift from the others the
moment the format changes.

**Why it matters:** correlation-key normalization logic duplicated across
several independent modules is exactly the kind of thing that looks
identical at three call sites today and silently diverges the day one of
them is updated and the other two are missed.

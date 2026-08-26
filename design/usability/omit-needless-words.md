---
name: omit-needless-words
type: standard
description: Cut UI copy hard — happy talk, instructions, and welcome text are usually pure overhead once a design is actually self-evident.
---

Most words on a screen are there to compensate for something the design
should already be communicating on its own. Krug (*Don't Make Me Think*)
puts a number on the instinct: cut what you've written by half, then cut
what's left by half again — and most of the time, nothing important is
lost.

The categories worth cutting first:
- **Happy talk** — friendly preamble before the actual content ("Welcome!
  We're so glad you're here. Take a look around and let us know if you
  have any questions!"). It delays the thing the user came for and reads
  as filler the moment a scanning eye passes over it.
- **Instructions** — if a control needs a sentence of explanation to be
  used correctly, that's a sign the control itself isn't self-evident
  yet ([[dont-make-me-think]]); fix the control before writing the
  instruction, since the instruction is the one thing most likely to be
  skipped by the scanning user who needed it most.
- **Redundant restatement** — a heading, then a paragraph restating the
  heading in longer form, then a bullet list restating the paragraph.
  Pick the one form that carries the information and delete the rest.

This is [[purposeful-silence]] applied to copy: every sentence on a
screen is competing for attention with the one sentence the user
actually needs, and padding makes that one sentence harder to find, not
easier.

**Why it matters:** a scanning user pays a fixed, small attention budget
per screen regardless of how much text is there — extra words don't add
information for that user, they dilute the words that do.

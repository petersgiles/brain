# Design Notes — Index

Design's counterpart to [`architecture/`](../architecture/README.md): a
distilled, cheaply-consumable guide to visual and UX design, not just
software structure. Same rules as that folder — one idea per file,
frontmatter (`name`, `type`, `description`), cross-linked with
`[[slug]]` — so an agent can pull in exactly the ideas relevant to a
task instead of reading a source book cover to cover.

## Usability

- [Don't make me think](usability/dont-make-me-think.md) — a screen
  should be self-evident, not just figure-out-able.
- [Scanning, not reading](usability/scanning-not-reading.md) — design for
  a user hunting for one thing, not reading every word.
- [First impression in seconds](usability/first-impression-in-seconds.md)
  — what is this, what can I do, why should I care — answered instantly
  or the user leaves.
- [Omit needless words](usability/omit-needless-words.md) — cut happy
  talk, instructions, and redundant restatement hard.
- [Clear wayfinding](usability/clear-wayfinding.md) — any single screen,
  landed on cold, should say where you are and how to get anywhere else.
- [Test early and often](usability/test-early-and-often.md) — a little
  testing constantly beats a lot of testing once.
- [Accessibility is usability](usability/accessibility-is-usability.md) —
  not a compliance pass bolted on after, the same usability work applied
  to more situations.

## Color

- [Sanzo Wada's *A Dictionary of Color Combinations*](color/sanzo-wada.md)
  — history, the interactive dictionaries built on it, and 12 curated
  starter combinations (name + hex) ready to use directly.

## Maintaining this folder

- One idea per file. A README entry is a pointer, never inline content.
- Give every file frontmatter (`name`, `type`, `description`) so it reads
  the same way an `architecture/` file does.
- Distill a source into original wording — don't reproduce a
  copyrighted book's text directly (see the ASD-STE100 note in the repo
  root README for why this matters here).
- Add a new topic directory once there's more than one file's worth of
  material; a single new idea can be a file at the top level until then.

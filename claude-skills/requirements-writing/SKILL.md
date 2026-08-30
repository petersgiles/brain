---
name: requirements-writing
description: "Use when writing or reviewing requirements, a spec, user stories, or a backlog — for any project, e.g. the pronounce app. Writes individual requirements in EARS syntax and prioritizes with PABLO (is this task worth doing), INVEST (is this story well-formed), MoSCoW (rank well-formed stories). Enforces one hard rule: the document states current truth only, never the history of how it was drafted or revised. Triggers: write requirements, write a spec, requirements doc, user stories, backlog, prioritize these, EARS, MoSCoW, INVEST, PABLO."
version: 0.1.0
---

# Requirements Writing

Operational checklist for this skill. Full rationale for every rule below
lives in `~/brain/requirements/` — read a linked file there when the
"why" matters, not just the "what."

## The one rule that overrides everything else

**Never narrate the drafting process inside the document.** No "this
section was added after further discussion," no "originally we
considered X," no summary of the conversation that produced the spec.
State the current truth about the system only. History of *how* a
requirement changed belongs in a commit message or changelog, not in the
spec body.

Full rationale:
`~/brain/requirements/writing/specs-describe-the-system-not-their-authorship.md`

## Writing one requirement — EARS syntax

Fixed sentence shape:

    While <optional precondition>, when <optional trigger>, the <system>
    shall <response>.

Only `the <system> shall <response>` is mandatory. `shall` means a
binding requirement — don't use it for description or aspiration.

Five patterns:

| Pattern | Keyword | Example |
|---|---|---|
| Ubiquitous | (none) | The system shall be accessible via HTTPS. |
| Event-driven | when | When the payment is received, the app shall send a notification. |
| State-driven | while | While in maintenance mode, the software shall block all user logins. |
| Unwanted behaviour | if...then | If the password is entered incorrectly, the app shall display an error message. |
| Optional feature | where | Where the Bluetooth module is present, the system shall support wireless pairing. |

Full detail: `~/brain/requirements/writing/ears-syntax.md`

## Prioritizing a backlog — apply in this order

1. **PABLO** — is this task worth doing at all: Purpose, Advantage,
   Benefit, Longevity, Outlay.
2. **INVEST** — is this one story well-formed: Independent, Negotiable,
   Valuable, Estimable, Small, Testable. Split a story that fails Small
   or Independent rather than force-fitting it.
3. **MoSCoW** — rank well-formed stories for a burndown: Must have /
   Should have / Could have / Won't have (this time).

Full detail:
`~/brain/requirements/prioritization/pablo.md`,
`~/brain/requirements/prioritization/invest.md`,
`~/brain/requirements/prioritization/moscow.md`

## Identifying and tagging requirements

- One requirement per file. Frontmatter carries `id`, `tags`, and
  `moscow` — a requirement's own frontmatter means its own file.
  Full rationale: `~/brain/requirements/writing/one-requirement-per-file.md`
- ID: dumb, sequential, context-prefixed (`HOST-001`, `LANG-014`).
  Assign once, never renumber or reuse.
  Full rationale: `~/brain/requirements/writing/stable-requirement-ids.md`
- Tags: the owning module/context plus any cross-cutting concern, drawn
  from the project's glossary, not invented per file.
  Full rationale: `~/brain/requirements/writing/requirement-tags.md`,
  `~/brain/requirements/writing/requirements-glossary.md`
- Index every ID in a lookup table (ID, tags, MoSCoW, one-line text,
  link) so a requirement can be found by ID alone.

## Output shape

- One EARS sentence per requirement file, grouped into a directory per
  feature/capability.
- Frontmatter: `id`, `tags`, `moscow`.
- A lookup table indexing every ID.
- No prose about how the list was produced — see the rule above.

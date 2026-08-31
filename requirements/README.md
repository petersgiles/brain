# Requirements Notes — Index

Requirements' counterpart to [`architecture/`](../architecture/README.md)
and [`design/`](../design/README.md): how to write and prioritize
requirements, not just how to structure or style the system itself. Same
rules as those folders — one idea per file, frontmatter (`name`, `type`,
`description`), cross-linked with `[[slug]]`.

## Writing

- [Specs describe the system, not their authorship](writing/specs-describe-the-system-not-their-authorship.md)
  — a spec states current truth; process/revision narrative belongs in
  commit messages, not the document.
- [EARS syntax](writing/ears-syntax.md) — the fixed sentence shape
  ("While..., when..., the system shall...") for writing one requirement.
- [Stable requirement IDs](writing/stable-requirement-ids.md) — a
  permanent, dumb, sequential ID (context-prefix + number) assigned once,
  never reused or renumbered.
- [Requirement tags](writing/requirement-tags.md) — a small controlled
  set of concern labels in frontmatter, separate from the ID, so
  classification can change without touching identity.
- [One requirement per file](writing/one-requirement-per-file.md) — a
  requirement's own frontmatter means its own file, indexed from a
  lookup table.
- [Requirements glossary](writing/requirements-glossary.md) — bounded
  context names and tags come from one authoritative project glossary,
  not invented ad hoc per file.
- [Decision record template](writing/decision-record-template.md) — a
  MADR variant (Title/Status/Problem/Decision/Consequences) with
  Context renamed to Problem, to stop decisions from citing today's
  implementation files instead of the durable problem.

## Prioritization

Applied roughly in this order when building a backlog: PABLO decides
whether a task earns a spot at all, INVEST checks a story is well-formed,
MoSCoW ranks well-formed stories against each other.

- [PABLO](prioritization/pablo.md) — Purpose, Advantage, Benefit,
  Longevity, Outlay: is this task worth doing at all.
- [INVEST](prioritization/invest.md) — Independent, Negotiable, Valuable,
  Estimable, Small, Testable: is this one story well-formed.
- [MoSCoW](prioritization/moscow.md) — Must/Should/Could/Won't have: an
  explicit, agreed cut line for a burndown.

## Maintaining this folder

- One idea per file. A README entry is a pointer, never inline content.
- Give every file frontmatter (`name`, `type`, `description`).
- Add a new topic directory once there's more than one file's worth of
  material; a single new idea can be a file at the top level until then.

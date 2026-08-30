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

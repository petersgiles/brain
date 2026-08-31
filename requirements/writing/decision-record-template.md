---
name: decision-record-template
type: standard
description: The decision-record template — Title, Status, Problem, Decision, Consequences — a MADR variant with Context renamed to Problem.
---

Based on MADR (adr.github.io/madr), with one deliberate change: the
section MADR calls "Context" is **Problem** here. "Context" invites
describing today's situation, including whatever the current
implementation happens to look like. "Problem" forces a crisp statement
of the actual technical or domain tension driving the choice —
independent of which files or libraries currently exist.

Fields:

- **Title** — a short name with a permanent, dumb, sequential ID (see
  [[stable-requirement-ids]]), e.g. `DEC-003: ...`.
- **Status** — Proposed, Accepted, or Superseded.
- **Problem** — the forces and constraints driving the choice, as a
  durable technical or domain fact. Not "file X currently does Y" — a
  proof-of-concept's files get renamed, moved, or rewritten; the actual
  problem (an algorithm's constraint, a domain rule, a cross-cutting
  requirement) usually outlives them. Reference requirement IDs freely —
  they're the durable spec — but avoid citing a specific implementation
  file path as the reason a decision exists.
- **Decision** — the chosen option, in active voice.
- **Consequences** — trade-offs, both benefits and liabilities, that
  follow *for the system*. Not a note that no new requirements were
  needed, or that this decision resolves some other open item — those
  are facts about the document set, not the system, and go stale the
  moment another document changes.

**Why it matters:** a decision record is read long after the code that
motivated it has been rewritten. Citing today's file names, or the
author's own private tooling, ties the record's meaning to something a
future reader — including a future agent working from this record alone
— has no access to and no reason to care about. See
[[specs-describe-the-system-not-their-authorship]].

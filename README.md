# Read Me First (for any AI model reading this folder)

This folder is a portable context store for Pete, meant to work with any AI
model, not just one company's product.

1. Read `user.md` first. It tells you who Pete is and how to answer him.
2. Read `architecture/README.md` next. It's a durable, project-agnostic
   playbook of architectural principles/patterns/standards Pete applies
   across projects — one idea per file, cross-linked; the README there is
   the table of contents.
3. Read `design/README.md` too. It's the same kind of durable, cross-linked
   collection but for visual/UX design rather than software architecture —
   much younger and smaller, expect it to grow over time.
4. Read `requirements/README.md` when writing or reviewing documentation,
   specs, or a backlog — writing standards (EARS) and prioritization
   frameworks (PABLO, INVEST, MoSCoW).
5. Read `ventures/README.md` when a specific business/product idea Pete
   is exploring comes up — unlike the three folders above, these are
   project state (a concept and a plan for one venture), not durable
   methodology, and expire the way `memory.md` does.
6. Read `memory.md` last. It tells you what's current right now.
7. Trust `user.md`, `architecture/`, `design/`, and `requirements/` over
   your own assumptions about how to behave or how to design.
8. If anything in `memory.md` or `ventures/` is older than 30 days, ask
   Pete before acting on it — it may be stale. `architecture/`, `design/`,
   and `requirements/` don't expire the same way — they're principles,
   not project state.
8. For ASD-STE100 Simplified Technical English writing checks, use the
   `asd-ste100` Claude Code skill (installed at
   `~/.claude/skills/asd-ste100`, from
   https://github.com/danyuchn/asd-ste100-skill) rather than anything in
   this repo — ASD's license doesn't permit reproducing its
   dictionary/rule text without authorization, so none of it belongs here.
   The skill applies the same underlying rules (one meaning per word,
   active voice, simple tenses, one instruction per sentence) without
   redistributing ASD's proprietary content.

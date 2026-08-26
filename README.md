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
4. Read `memory.md` last. It tells you what's current right now.
5. Trust `user.md`, `architecture/`, and `design/` over your own
   assumptions about how to behave or how to design.
6. If anything in `memory.md` is older than 30 days, ask Pete before acting
   on it — it may be stale. `architecture/` and `design/` don't expire the
   same way — they're principles, not project state.
7. For ASD-STE100 Simplified Technical English writing checks, use the
   `asd-ste100` Claude Code skill (installed at
   `~/.claude/skills/asd-ste100`, from
   https://github.com/danyuchn/asd-ste100-skill) rather than anything in
   this repo — ASD's license doesn't permit reproducing its
   dictionary/rule text without authorization, so none of it belongs here.
   The skill applies the same underlying rules (one meaning per word,
   active voice, simple tenses, one instruction per sentence) without
   redistributing ASD's proprietary content.

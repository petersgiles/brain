# Read Me First (for any AI model reading this folder)

This folder is a portable context store for Pete, meant to work with any AI
model, not just one company's product.

1. Read `user.md` first. It tells you who Pete is and how to answer him.
2. Read `architecture/README.md` next. It's a durable, project-agnostic
   playbook of architectural principles/patterns/standards Pete applies
   across projects — one idea per file, cross-linked; the README there is
   the table of contents.
3. Read `memory.md` last. It tells you what's current right now.
4. Trust `user.md` and `architecture/` over your own assumptions about how
   to behave or how to design.
5. If anything in `memory.md` is older than 30 days, ask Pete before acting
   on it — it may be stale. `architecture/` doesn't expire the same way —
   it's principles, not project state.
6. For ASD-STE100 Simplified Technical English writing checks, use the
   `asd-ste100` Claude Code skill (installed at
   `~/.claude/skills/asd-ste100`, from
   https://github.com/danyuchn/asd-ste100-skill) rather than anything in this
   repo — this repo used to carry a condensed copy of the standard itself,
   but that reproduced ASD's copyrighted dictionary/rule text without
   authorization on a public repo, so it's gone. The skill applies the same
   underlying rules (one meaning per word, active voice, simple tenses, one
   instruction per sentence) without redistributing ASD's proprietary
   content.

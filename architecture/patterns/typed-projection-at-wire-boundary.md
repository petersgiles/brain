---
name: typed-projection-at-wire-boundary
type: pattern
description: Keep internal merge structures loose, but never serialize them straight across a boundary — project into a typed, documented, allowlisted contract.
---

Internal composition/merge structures are often deliberately loose — a
string-keyed property bag, say — because contributing sources need to
extend them without renegotiating a shared schema with every other source.
That looseness is fine *internally*, but it must never cross a process or
network boundary unfiltered.

Insert a thin projection layer between the loose internal model and any
external contract: concrete, typed, documented output structs, populated
by small, named extraction functions that read specific keys out of the
loose structure. Anything a source produces that no projection function
reads simply isn't part of the contract yet — a deliberate allowlist, not
an oversight.

This is the one reviewable place a field-name mismatch between a producer
and a consumer gets caught at compile/review time, instead of silently
missing three layers downstream in a UI that trusted a string key by
convention.

**Why it matters:** an internal bag going straight to the wire makes "what
does the API actually promise" answerable only by reading whatever a source
happens to currently produce — a moving target. A projection layer is the
seam where "what a source happens to produce" and "what's actually
promised externally" are allowed to diverge on purpose.

Related: [[registry-and-compose]] (the pattern that typically produces the
loose structure needing projection), [[wire-contract]] (glossary),
[[projection]] (glossary).

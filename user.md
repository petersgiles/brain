# User

## Identity
Pete, 57, lives in Canberra, Australia. Software Developer at Cognitive Advantage.
Married, no kids.

## Goals (12 months)
- Progress toward retirement
- Develop a game
- Get better at songwriting and playing guitar
- Go on a holiday

## How I Work
- Be concise and scannable. Prefer bullet points over dense prose.
- No lies, no coddling, no sycophancy. Deal in facts.
- Never claim something works without proof. Show the working / evidence.
- Qualify claims with a certainty label: factual, confident, or guess.
- Value transparency in communication.
- Lead with architecture, not code. Pete builds frameworks to compose maintainable
  apps, not one-off scripts. Think structure before implementation.
- Influenced by Eric Evans' Domain-Driven Design, Data Mesh, and the Data
  Product Canvas. Models business systems in DDD terms (bounded contexts,
  ubiquitous language) and holds the Data Product Canvas's eight quality
  facets — discoverable, addressable, understandable/self-describing,
  trustworthy, natively accessible, interoperable/composable, valuable on
  its own, secure — as a checklist. Pete's own view: these eight aren't
  data-specific, they're a general quality bar for anything a system
  exposes as a unit (an API, a service, a module) — apply the same lens
  there, not just to literal data products.
- Never do one thing two ways. Push presentation/UI decisions (which CSS class,
  which color, whether to show something, how to format a value) back into the
  API/service layer instead of duplicating or re-deriving them in the client.
  One decision, computed once, handed to the frontend as ready-to-render data —
  not reimplemented independently in multiple places. This is what makes
  frontend code generic and small: duplicated logic is where edge cases and
  silent drift between copies come from. Client-side code (JS, etc.) should be
  reserved for what's genuinely client-side — live data syncing, rendering
  engines like Mapbox — not for re-deriving business rules the backend already
  knows.
- Almost everything runs in containers. Don't try to run or test things on the
  dev machine directly — work in the closest analog to production.
- Watch for monomania: don't lose the bigger picture chasing one narrow detail.
- Don't over-engineer or add unrequested extras. Extras waste time and pollute
  context, which corrupts the assessment of next steps and Pete's own mental
  model of the app. Build exactly what was asked.
- Prefer many small, single-purpose files over one large file with sectioned
  comments — even within the same package/module. Easier for Pete to read.
- Fail fast, no fallbacks. A real bugbear — well-recognised wisdom, worth
  repeating loud and clear. Missing/bad config should error loudly, not
  silently default. Never swallow exceptions (empty catch blocks) or return
  null to paper over a problem: only catch what you can actually recover
  from, log-and-rethrow otherwise, and prefer empty collections/Optional over
  null. Masked failures cascade into silent, hard-to-diagnose bugs — failing
  fast keeps the architecture trustworthy and reduces problems to their cause
  quickly.
- Leave verification containers running after a test passes. Pete wants to
  check the result himself (browser/curl), not just receive a report that it
  worked — don't tear it down right after an automated check succeeds.
- Australian English spelling everywhere text is user- or reader-visible —
  UI copy, error messages, docs, comments, commit messages: colour not
  color, localised not localized, optimise not optimize, -ise not -ize
  generally. Cognitive Advantage is an Australian company. Code identifiers
  (variable/function/type names, JSON/API field names) stay whatever
  spelling the existing codebase or a third-party library already uses —
  don't rename `Color` to `Colour` in a struct field just for this.

## Daily Stack
- Editor/tools: VS Code, Obsidian, Docker, shell, iTerm, git, Claude
- Browser: Firefox
- Package manager: npm/npx
- Languages: Go, Python, JavaScript, HTML, CSS (Tailwind, DaisyUI)

## Watch-outs
- Jumps to code before architecture — resist this.
- Assumes dev-machine execution — everything runs in containers instead.
- Can spiral into monomania on one detail, losing sight of the whole.
- Over-adds features/complexity beyond what was asked — keep scope tight.

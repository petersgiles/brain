---
name: layered-secret-scanning
type: pattern
description: Catch credentials before they enter version control with two layers — a local pre-commit scanner and a CI scan on every push — since neither alone is sufficient, and baseline pre-existing findings so introducing the scan doesn't create permanent, ignorable noise.
---

Two layers, not one: a local pre-commit hook that scans staged changes
before a commit is created, and a CI job that runs the same scan on
every push/PR regardless of what ran (or didn't) locally. Neither layer
alone is sufficient. A local hook only fires for contributors who've
actually activated it, and is trivially bypassable (skip the one-time
setup, or a flag that skips hooks entirely) — it's a fast feedback loop
and an onboarding forcing-function, not enforcement. CI catches
everything the hook missed, but by itself only reports red after a bad
commit already exists; it doesn't stop one from being made.

**On real enforcement**: the only way to make this genuinely
non-bypassable is a server-side gate — rejecting the push/merge outright
if the scan fails, independent of any contributor's local setup. Whether
that's available depends entirely on the hosting platform and plan; where
it isn't, be honest about what you actually have (a strong local nudge +
a visible CI signal) rather than presenting it as a real gate it isn't.
Don't let "we can't fully enforce it" become a reason to skip the two
layers that *are* achievable — partial coverage against an entire class
of mistake is still worth having.

**Missing tooling is a failure, not a skip**: if the scanner itself
isn't installed, the local hook should refuse the commit with an install
pointer, not silently let it through with a warning. A warning-and-allow
hook quietly degrades to "works for whoever remembered to install it,"
which stops being visible the moment it happens. Treating absent
tooling as the same failure mode as a real finding is what actually
makes the hook function as onboarding pressure rather than a suggestion.

**Baseline before you enforce forward**: introducing this into a repo
with real history almost always surfaces pre-existing findings.
Rewriting history to scrub them is a separate, heavier decision (it
breaks every existing clone and requires everyone to re-clone) — don't
let that decision block turning scanning on at all. Instead, allowlist
the specific already-known findings (by commit/fingerprint, with a note
on why) so the scan starts clean and fails only on genuinely *new*
findings going forward. A scan that's permanently red from day one
because of accepted historical debt trains everyone to ignore it, which
defeats the entire point.

**Why it matters:** a credential committed once is compromised
permanently — rotation is the only real fix, and it's after-the-fact
regardless of how good the scanning is. The two layers here are about
shrinking the window between "credential typed into a file" and
"caught," and about making the catch happen by construction (tooling)
rather than by hoping code review notices a long random-looking string
in a diff.

See [[boundary-validation]] — the commit/push boundary is exactly where
a credential should be caught, not left to review discipline or
discovered later by chance. See [[fail-fast-no-fallbacks]] for the same
reasoning applied to the "missing tooling blocks the commit" choice
above.

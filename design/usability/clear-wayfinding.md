---
name: clear-wayfinding
type: standard
description: A user landing on any single screen, with no other context, should be able to tell where they are, what the whole thing contains, and how to get anywhere else in it.
---

Krug's "trunk test" (*Don't Make Me Think*): drop a user into any one
screen at random, with no path that got them there, and check whether
they can answer — where am I? what's the overall structure of this
thing? what's here on this specific screen? where have I been, where can
I go? Passing this test everywhere is what "navigation" actually means;
a nav bar that only works when arrived at from the home screen fails it.

Requirements that fall out of the test:
- A **persistent identity and section indicator** on every screen — the
  product/site name and which section this is, not just on the entry
  screen.
- A **consistent navigation structure** in the same place, in the same
  form, on every screen — consistency is what lets a user stop consciously
  navigating and start recognizing.
- A **"you are here" signal** — a highlighted nav item, a breadcrumb, a
  header — so the current location is never ambiguous from the current
  screen alone.
- A **way back to the top/home** from anywhere, since a lost user's
  first instinct is to reset to a known point, not to guess forward.

**Why it matters:** most navigation isn't used start-to-finish along the
path the designer imagined — users arrive from search results, shared
links, or by jumping around — so the wayfinding elements have to work
from anywhere, not just from the front door.

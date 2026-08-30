---
name: ears-syntax
type: standard
description: EARS (Easy Approach to Requirements Syntax) — the fixed sentence shape every individual requirement statement should follow.
---

EARS is the standard sentence structure for writing one requirement.
Every requirement follows the same fixed order:

    While <optional precondition>, when <optional trigger>, the <system>
    shall <response>.

Only `the <system> shall <response>` is mandatory — precondition and
trigger are included only when they apply. `shall` is reserved for a
binding requirement; don't use it for description or aspiration.

**The five patterns**, by when the requirement applies:

- **Ubiquitous** — always true, no condition needed.
  *The system shall be accessible via HTTPS.*
- **Event-driven** — fires on a specific trigger (`when`).
  *When the payment is received, the app shall send a notification.*
- **State-driven** — active for as long as a state holds (`while`).
  *While in maintenance mode, the software shall block all user logins.*
- **Unwanted behaviour** — a fault or error condition (`if...then`).
  *If the password is entered incorrectly, the app shall display an
  error message.*
- **Optional feature** — depends on an optional component being present
  (`where`).
  *Where the Bluetooth module is present, the system shall support
  wireless pairing.*

**Why it matters:** the fixed structure forces every ambiguity a
requirement could hide — what triggers it, what state it depends on, what
the system actually does in response — into an explicit, separately
named slot. That same explicitness is what makes each requirement
directly testable: precondition and trigger become test setup, `shall
<response>` becomes the assertion.

**How to apply:** write the actual requirements list in EARS sentences.
Don't use EARS as a lens for restating context, rationale, or narrative —
see [[specs-describe-the-system-not-their-authorship]] for why that
belongs elsewhere.

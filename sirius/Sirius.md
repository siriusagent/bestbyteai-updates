<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.007

**Alpha channel release.** Sirius's core product surfaces and signed update
path are stable enough for regular use. The alpha label remains a pre-1.0
release channel — updates may still refine behavior and compatibility — but
this is a user release, not an installation or packaging test.

This release continues the Computer Use hardening train after
v0.1.1-alpha.006: replay-safety identity gaps, tool-family prompt parsing,
SkyLight delivery correctness, and momentary-focus typing truncation — plus
CLI-agent Settings fixes and a no-progress replan change that keeps surface
pivots available.

## Fixed

- **Coordinate replay identity no longer fails open on int vs float literals
  (BUG-376).** An unconfirmed `click_point(x=800, y=600)` now blocks a replay
  of `click_point(x=800.0, y=600.0)` (and the same for `drag`). Numeric
  identity is canonicalized per value rather than per literal spelling.

- **One unconfirmed scroll no longer blocks every later scroll in that window
  (BUG-377).** Scroll identity now carries `direction` and `amount`, so a
  different gesture (including scrolling back the other way) is allowed while
  an identical pair still fails closed. This is the common canvas/PDF/map
  case where scroll stays honestly `unconfirmed`.

- **A prohibition no longer swallows the tool the user asked for next
  (BUG-378).** "Do not use the browser, instead use `computer_use_scroll`"
  kept denying the prescribed tool because negation capture ran to the
  sentence terminator. Clauses now stop at `;` / `—` and at contrastive
  markers (`instead`, `then`, `but`, …); comma-separated deny lists still
  span commas.

- **An exclusivity clause no longer matches a family named inside a
  condition or a negation (BUG-379).** "Use the browser only when computer
  use tools fail" no longer resolves to exclusive `computer_use` and removes
  the browser family. Conditional and negated phrasings are skipped; a
  genuine "use only … tools" restriction still applies.

- **Momentary focus recovery no longer truncates typing at 32 characters
  (BUG-380).** Agent-caused window activation was mistaken for a user
  takeover, so longer `computer_use_type` calls aborted after the first
  chunk with `blocked: user_interruption`. The takeover baseline now rebases
  onto the target when the runner itself activated it.

- **SkyLight delivery no longer posts every event twice (BUG-381).** The
  additive tier was posting through both `SLEventPostToPid` and
  `CGEvent.postToPid`, so AppKit targets that accept both channels duplicated
  typed text and turned coordinate clicks into synthetic double-clicks. Each
  site now uses exactly one channel (SkyLight when available, else public
  `postToPid`).

- **Codex CLI updates no longer leave Settings showing "Install failed"
  (BUG-374).** Detection prefers the platform-native executable over a stale
  user-local PATH shim after a successful install/update.

- **Enabling the first CLI subagent in a live session no longer hot-loads
  into an abandoned registry (BUG-375).** An empty caller-supplied
  `AgentRegistry` is preserved, so Settings enablement is visible to
  `subagent_dispatch` without starting a new session.

- **No-progress replan no longer hides the whole Computer Use family.** Only
  composed in-window primitive verbs are withdrawn on a stall, so the model
  can still pivot to another surface (launch/activate/observe desktop, …)
  instead of being stranded mid-task.

## Notes

- **Sparkle build version** is `132` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `131` or earlier will offer
  this release.
- This release changes both the Swift host (Computer Use delivery, focus
  recovery, CLI Agents Settings) and Python engine code (replay identity,
  tool-family parsing, replan hiding). The signed core-runtime feed is
  refreshed as `0.1.1-alpha.007`.

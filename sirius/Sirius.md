<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.010

**Alpha channel release.** Sirius's core product surfaces and signed update
path are stable enough for regular use. The alpha label remains a pre-1.0
release channel — updates may still refine behavior and compatibility — but
this is a user release, not an installation or packaging test.

This release adds a full reliability and quality pass for dictation and Read
Aloud, makes canvas interactions visual and point-accurate, strengthens
post-compression recovery, and updates Markdown rendering.

## Voice input and Read Aloud

- **Dictation now uses bounded realtime audio transports, selection-aware
  editing, per-session language and context, and honest backend fallback.**
  Sending or moving conversation focus waits for the authoritative final
  correction, failed backend preparation falls through before capture starts,
  and ordinary large first callbacks no longer report a false overrun.
- **Read Aloud now speaks the semantic document rather than presentation
  debris.** Structured blocks are emitted in bounded, language-aware chunks
  with safe pause, resume, restart, and stop behavior.
- **Voice Settings uses the shared native macOS Settings layout.** Recognition
  and voice controls stay compact while permission status remains centralized
  in Permissions & Security.

## Browser and canvas interactions

- **Canvas turns can reason from the completed action immediately.** Sirius
  injects the visible viewport as provider-only visual context with explicit
  image-pixel to viewport-coordinate mapping, avoiding a redundant screenshot
  round trip.
- **Coordinate clicks validate the exact requested point.** Point reachability
  replaces whole-element coverage guesses, and pixel-only interactions no
  longer require fabricated DOM mutation conditions.

## Reliability

- **Post-compression recall enforcement now persists across turns (BUG-391).**
  Sirius keeps the active-session recovery gate and cumulative miss count until
  the required recent-transcript `session_search` succeeds.
- **OpenAI-compatible turns accept the Computer Use transaction schema
  (BUG-390).** Function validation no longer fails before generation, while
  native intent validation remains fail-closed.

## Markdown rendering

- **Sirius now ships [SiriusMarkdown
  0.6.23](https://github.com/mikhutchinson/SiriusMarkdown/releases/tag/0.6.23).**
  Activatable links keep a visible fallback glyph, invisible favicons cannot
  replace it, and tight line heights no longer clip `p`, `g`, or `q`
  descenders. The package release passed 948 tests and its full visual/product
  gate.

## Notes

- **Sparkle build version** is `135` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `134` or earlier will offer
  this release.
- This release changes both the Swift host and the Python engine. The signed
  core-runtime feed is refreshed as `0.1.1-alpha.010` so the app, appcast, and
  Python runtime component remain release-synchronized.

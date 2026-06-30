<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.98

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This is a **hotfix release** over alpha.97. It tightens native computer-use
transcript rendering, screenshot target selection, and sensitive AX value
redaction.

## Changes

- **Computer-use transcript noise is grouped.** Adjacent `computer_use_*`
  events now coalesce into a desktop-action group instead of filling the
  transcript with repeated one-line observations. Expanding the group preserves
  every individual audit line and popover.
- **Safari and Terminal screenshots avoid menu-bar crops.** App-owned menu-bar
  strips such as `1728x33 @ 0,0` are filtered from discovery and rejected as
  exact ScreenCaptureKit targets, so capture falls back to the real content
  window for the app.
- **OAuth-style address/search values are redacted.** Browser AX fields that
  expose callback parameters such as `code`, `access_token`, `id_token`,
  `refresh_token`, or `state` are treated as sensitive before projection,
  persistence, or transcript popovers.
- **Regression coverage expanded.** Focused Swift tests pin desktop grouping,
  menu-bar frame filtering, OAuth callback redaction, and historical replay
  compatibility.
- **The distributable build defaults now target alpha.98 / build 98.**

## Distribution

- Published as monotonic Sparkle build 98.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

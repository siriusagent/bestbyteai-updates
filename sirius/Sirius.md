<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.27

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Rebuilds the Appearance preferences pane with explicit settings groups instead
  of raw macOS Form rows, fixing overlap between the Light / Dark / Auto cards
  and their selected outline.
- Keeps theme preview content inside its card bounds at the default Preferences
  width and when the window is resized.
- Removes row-wide Appearance tooltips that could paint over adjacent controls.
- Hides the Terminal theme picker's internal label so the row shows only the
  selected value.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

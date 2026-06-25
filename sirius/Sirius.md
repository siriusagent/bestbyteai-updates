<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.83

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Normalize Settings picker layout.** Agent & Subagents bounded scalar rows now
  use the same menu-style picker shape as Background Work, while Temperature
  remains a slider. The pane no longer mixes spinner steppers with picker menus
  for the same class of controls.
- **Align Settings controls to a shared right edge.** Root Settings panes and
  supporting sheets now reserve the same trailing control frame for scalar
  controls, so pickers, sliders, toggles, and remaining fixed-width steppers land
  on a consistent right edge across Settings.
- **Document the Settings control discipline.** The Agent & Subagents and
  Appearance settings specs now describe when to use menu pickers, sliders,
  segmented controls, and fixed-width steppers.
- **The distributable build defaults now target alpha.83 / build 83.**

## Distribution

- Published as monotonic Sparkle build 83.
- Ships a refreshed signed core-runtime feed aligned with alpha.83.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

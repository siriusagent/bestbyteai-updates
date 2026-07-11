<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.114

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This release repairs the provider/model controls that shipped with alpha.113
and brings the surrounding Settings rows back to a consistent native macOS
layout.

## What's new

- **The composer model control is compact and capability-aware.** The closed
  pill keeps the provider mark, model, and selected effort together without a
  long empty track or mismatched typography.
- **The model menu follows configured state.** Only configured providers appear
  in the selection path. A quiet **Manage Providers…** link opens Network &
  Providers for adding or changing backends.
- **Models and reasoning effort stay connected.** The menu is a searchable flat
  model list. Models with exact live reasoning metadata disclose their effort
  choices inline; unsupported or non-live models remain plain rows.
- **Reasoning labels are human-facing.** Provider wire values such as `xhigh`
  display as **Extra High** while Sirius preserves the original value for
  validation, persistence, and provider requests.
- **Network & Providers remains inline.** Primary and independent Background
  controls no longer fall into a three-row stack at the supported Settings
  width. Provider, model, optional effort, refresh, and configure stay on one
  row.
- **Short selections no longer absorb empty space.** Provider/model/effort
  controls are intrinsic and bounded; unused row width belongs to the layout
  spacer instead of producing an oversized `gpt-5.6-luna` picker.
- **Settings row alignment is consistent.** Appearance and General → Logging
  now use the shared Settings row chrome and trailing control alignment used by
  the rest of the app. Logging Level is a compact menu picker.

## Reliability and compatibility

- Composer model+effort changes are applied as one capability-validated update,
  preventing stale model state from accepting an unsupported effort.
- Live catalogue discovery, explicit refresh, provider persistence, background
  mirror behavior, session-only composer overrides, and next-turn hot-swap are
  unchanged.
- The public app continues to install the signed core runtime from the Sirius
  runtime feed after EULA acceptance; no Python source seed is bundled in the
  DMG.

## Notes

- **Sparkle build version** is `114` (`CFBundleVersion`), the primary comparison
  key for auto-update. Apps on `113` or earlier will offer this build.
- The signed core-runtime feed is refreshed as `0.1.0-alpha.114` so the app,
  appcast, and runtime component remain release-synchronized.

<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.26

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Persists Appearance settings in `~/.sirius/config.toml` under `[appearance]`
  instead of writing new changes only to UserDefaults. Existing legacy defaults
  are imported on first load.
- Flushes pending Settings and Appearance writes before app quit and before a
  Sparkle relaunch, so recent edits are not lost during update installation.
- Narrows Settings autosaves by category. Profile edits no longer trigger
  provider, goal, or permission runtime hooks; goal edits only reapply goal
  settings.
- Keeps Preferences selection stable with a fixed sidebar width and wraps theme
  choices adaptively in the Appearance pane.
- Updates the Ollama Compatible Model Hub to keep oversized GGUF rows visible
  with `Fits this Mac`, `May be slow`, or `Won't fit` labels. Ranking now keeps
  fit, capability, quant, and size tier ahead of popularity signals.
- Adds stale-cache compatibility for older Ollama hub snapshots while bumping
  the live hub schema.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

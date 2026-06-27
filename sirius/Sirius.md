<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.84

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Modularize SessionController and SiriusRuntime.** Per-window session control
  and the shared runtime are split into domain-focused extension files
  (lifecycle, turn execution, event ingestion, background wake, permissions,
  hot reload, and related concerns) so each concern stays in a focused module
  without changing the production session path.
- **SiriusMarkdown is updated to 0.5.12.** The app bundle picks up the current
  Markdown renderer line for transcript, plan artifact, and DiffTree preview
  surfaces.
- **The distributable build defaults now target alpha.84 / build 84.**

## Distribution

- Published as monotonic Sparkle build 84.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

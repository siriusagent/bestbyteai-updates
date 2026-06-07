<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.19

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Adds Help -> Report Bug, a native local-first bug-report prototype that
  captures the observed issue, session/screenshot context, visible error text,
  recent app logs, recent SwiftPython pool telemetry, and an optional
  `/usr/bin/sample` into a timestamped local bundle and ZIP.
- Uses the configured Sirius background model, when available, to generate a
  grounded report from the collected evidence. The report prompt separates
  logged facts from likely interpretation and avoids inventing paths,
  timestamps, or causes.
- Opens a bounded GitHub issue draft and keeps the full local ZIP as the
  attachment bundle, avoiding any Cloudflare/R2 dependency for this prototype.
- Keeps the report window outside the known SwiftUI selection-overlay hang path
  by using AppKit-backed multiline text views.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

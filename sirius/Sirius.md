<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.10

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Updates the embedded SwiftPython runtime dependency to
  `swiftpython-commercial` `0.5.10`, picking up the ProcessPool respawn-budget
  hardening, identical-error fingerprint cap, and forced-cleanup socket
  interrupt fix from SwiftPython.
- Surfaces the new SwiftPython per-error respawn exhaustion reasons through
  Sirius worker-death banners with shortened SHA-256 fingerprints, so repeated
  worker failures are easier to diagnose.
- Recovers the first stale SwiftPython session-handle failure by rebuilding the
  session and retrying before any stream output reaches the transcript.
- Publishes signed core-runtime update metadata through Sparkle and the
  Components settings flow, so future Python-side Sirius agent fixes can ship
  without requiring a fresh DMG install.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.2-alpha.004

Alpha.004 is a focused host-app repair for two failures introduced by the
previous alpha.

## Older conversation pages no longer crash

- Loading an older page that contains assistant tool output no longer triggers
  a Swift dynamic-exclusivity abort in optimized builds.
- History prepend now reconstructs its transcript side indices in one local
  state and publishes that state atomically.
- The exact assistant/tool page is covered in both the normal Swift suite and
  an optimized Release regression gate.

## Fresh public installs recover the engine before boot

- A public no-seed app with an empty Sirius home now downloads and verifies the
  signed Sirius Engine before starting workers. It no longer falls through to
  `No module named 'sirius_agent'`.
- The recovered candidate retains the existing rollback contract and is
  committed only after the real worker fleet reports a successful bootstrap.

## Project loading always reaches a terminal state

- The Projects sidebar now distinguishes idle, loading, loaded, and failed
  queries independently from chat loading.
- Its first Python-backed query starts only after the signed managed runtime is
  ready, so a no-seed launch cannot strand a pre-bootstrap request.
- A failure stops the spinner and presents an accessible Retry action. A
  successful query with zero projects shows **No projects yet**.

## Notes

- Sparkle build version is `160` (`CFBundleVersion`). Apps on build `159` or
  earlier will be offered this release.
- The signed ABI-1 core runtime remains engine version `2026.08.30.4`; this
  release changes only the macOS host and reuses the already verified runtime
  feed.

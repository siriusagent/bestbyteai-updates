<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.97

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This is a **hotfix release** over alpha.96. It hardens native computer use and
the inline screenshot/capture rendering path before wider alpha testing.

## Changes

- **Computer-use coordinate actions are fixed.** Coordinate clicks no longer
  require a stale `snapshot_id`, while ref-backed clicks still require the
  observe snapshot that minted the ref. Window-relative click and drag
  coordinates are now mapped through the target window frame before dispatch.
- **Capture artifacts are safer.** Screenshot session directories sanitize
  session ids, and capture no longer falls back to a shared `computer-use/default`
  bucket when a bridge call has no real session id.
- **AX snapshotting is more defensive.** Accessibility point, size, and focused
  element reads now validate CoreFoundation value types before bridge casts, so
  malformed or surprising AX values degrade instead of crashing the host path.
- **Inline visual delivery is more robust.** Computer-use screenshot artifacts
  are promoted into provider visual context when possible, and fall back to
  file-only metadata when the image cannot be read.
- **Regression coverage expanded.** The release adds focused Swift and Python
  coverage for coordinate/ref contracts, capture cleanup, inline rendering,
  provider visual dispatch, and architecture boundaries.
- **The bundled Python core runtime refreshes with this build.** The signed
  core-runtime feed ships the updated `sirius_agent` package, including the
  computer-use fixes.
- **The distributable build defaults now target alpha.97 / build 97.**

## Distribution

- Published as monotonic Sparkle build 97.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

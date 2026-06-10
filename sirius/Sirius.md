<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.42

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixed browser webcam access in the shipped macOS app. The signed app now
  declares camera usage, carries the camera entitlement, and keeps media capture
  prompts on the native `WKWebView` app path.
- Updated the microphone privacy text to cover browser microphone capture as
  well as composer dictation.
- Added release-verifier checks for camera/microphone privacy strings, app media
  entitlements, and worker non-entitlement so the bundle contract cannot quietly
  regress.
- Improved Permissions & Security diagnostics for media capture. It now
  separates missing hardware from privacy state, showing "No camera detected" or
  "No microphone detected" before TCC status when a Mac has no capture device.
- Carries alpha.41 fixes forward, including CLI sub-agents and inline
  sub-agent answers in the transcript.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

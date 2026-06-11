<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.44

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixed browser observation for pages with active camera/video streams. Existing
  `browser_use_observe`, `browser_use_screenshot`, and `sirius_browser_describe`
  results now report visible active media streams, track state, dimensions, and
  bounded device labels when WebKit exposes them.
- Added a guard for WebKit bitmap snapshots that omit live video layers:
  screenshot results now carry `media_state` plus a capture note so Sirius does
  not claim there is no camera feed solely because the saved bitmap missed live
  media pixels.
- Kept the tool surface unchanged. There is no camera-specific browser tool;
  media awareness is part of the existing browser observation contract.
- Carries alpha.43 provider-auth fixes forward.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

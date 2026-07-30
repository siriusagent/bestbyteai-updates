<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.009

**Alpha channel release.** Sirius's core product surfaces and signed update
path are stable enough for regular use. The alpha label remains a pre-1.0
release channel — updates may still refine behavior and compatibility — but
this is a user release, not an installation or packaging test.

This release makes canvas and game interactions dependable when Sirius starts
in the background, and ensures provider changes immediately reach channel work
even when no conversation window is open.

## Browser and canvas interactions

- **Canvas-adjacent controls now receive the intended trusted click even when
  Sirius was not frontmost (BUG-386).** Browser transactions carry paired CSS
  coordinates with point-specific lineage, so distinct locations on one
  graphics surface remain distinct actions. Before posting the global HID
  event, Sirius activates its app and prepares the exact browser window and
  `WKWebView` responder. The transaction also rejects a condition that was
  already true before the mutation, while ordinary DOM controls retain their
  semantic click path.

## Provider and channel routing

- **Saving provider or authentication settings now rebinds worker-0 channel
  routing through the production save path (BUG-385).** Telegram and other
  generic channels no longer retain an obsolete API-key route after switching
  to ChatGPT OAuth. The rebind runs even with zero foreground sessions,
  preserves per-session overrides, and reports a worker-0 failure through the
  existing Settings error surface instead of claiming a successful hot-swap.

## Reliability

- **Tool-cycle detection is now split into focused browser, Computer Use,
  evidence, model, and detector modules.** The behavior remains on the same
  shared engine boundary, while the expanded focused suites make replay,
  no-progress, and evidence handling easier to validate independently.

## Notes

- **Sparkle build version** is `134` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `133` or earlier will offer
  this release.
- This release changes both the Swift host and the Python engine. The signed
  core-runtime feed is refreshed as `0.1.1-alpha.009` so the app, appcast, and
  Python runtime component remain release-synchronized.

<!-- sparkle-sign-warning:
IMPORTANT: This file is signed into the Sparkle appcast. Any modifications require re-running generate_appcast or sign_update before publishing.
-->
# SiriusMsg 0.0.1 (build 8)

Release update for recipe runtime wiring, generated SDK parity, and honest rich
messaging capability surfaces.

## Changed

- Wired saved recipes into the signed agent runtime so allowlisted inbound
  message, reaction, edit, and unsend events can trigger recipe actions through
  the existing service send path.
- Added shared recipe storage, hot reload, runtime health counts, and an app
  reload control so recipe edits take effect without restarting the agent.
- Published recipe runtime status and sanitized recipe adapter envelopes through
  the public protocol schema, Python SDK models, and TypeScript SDK models.
- Updated the Recipes app surface to separate enabled intent from agent-reported
  running state, group inbound and send capabilities by direction, and label
  webhook or schedule recipes as not running locally yet.

## Fixed

- Fixed the default artifact recipe so it has a real attachment placeholder and
  no longer ships as an enable-able actionless recipe.
- Preserved the `recipeNoActions` guard for user-authored draft recipes while
  allowing the fixed default artifact recipe to run when its capabilities are
  supported.
- Prevented disabled recipes from showing an enabled-looking recipe glyph in the
  app.
- Made generated Python SDK models carry the same source-of-truth and
  do-not-edit provenance header as TypeScript generated models.

## Verification

- SDK generated artifact check: passed.
- Swift test suite: passed.
- Python SDK tests: passed.
- TypeScript SDK build and tests: passed.
- App notarization: accepted by Apple notary service.
- DMG notarization: accepted by Apple notary service.
- Gatekeeper: accepted as Notarized Developer ID.
- DMG image verification: valid.
- Signed bundle verification: nested agent bundles `Python.framework`,
  `SiriusMsgHooks.framework`, and `SwiftPythonWorker` without Homebrew,
  user-home, checkout, private source, bytecode cache, or global
  `site-packages` linkage.
- Operational validation gate: passed with the notarized DMG path.

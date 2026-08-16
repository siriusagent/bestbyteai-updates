<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.026

Alpha.026 is a focused hotfix for background-task output recovery and updates
the native worker runtime to SwiftPython `0.6.0-duplex.7`.

## Background output hotfix

- **Captured output survives a task-revision race in the manager.** Sirius now
  refreshes the authoritative task snapshot and retries once with the current
  revision instead of decoding a typed stale response as a broken store.
- **Unavailable states tell the truth.** A task already pruned after its result
  was delivered and a missing output capture no longer claim that the SQLite
  task store could not be verified.
- **Retry advances authority.** Output retry reads the refreshed server row;
  navigation, session, and worker-lifetime fences continue to reject late data.

## Runtime update

- The app now ships the exact matched SwiftPython `0.6.0-duplex.7` Runtime,
  private Engine, and worker artifacts.
- Worker wire remains v6. The new backend-neutral accelerator contract is
  additive and capability-gated; this hotfix does not change Sirius provider,
  tool, permission, or accelerator selection behavior.
- SwiftPython also fixes a duplex playback-acknowledgement race that could lose
  the acknowledged output cursor during terminal publication.

## Verification

- Focused background-task manager tests cover stale-revision refresh/retry,
  pruned-task messaging, missing capture, malformed versions, and cancelled
  presentation authority.
- The full Swift host gate passed after a clean package rebuild.
- The checked-in SwiftPython public guide and standard interfaces match the
  immutable `0.6.0-duplex.7` commercial revision.
- Full host, package, signed-bundle, notarization, Gatekeeper, and public-feed
  evidence is required before this release is marked shipped.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 151 with the matching signed core-runtime feed.

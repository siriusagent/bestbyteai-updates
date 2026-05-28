<!-- sparkle-sign-warning:
IMPORTANT: This file is signed into the Sparkle appcast. Any modifications require re-running generate_appcast or sign_update before publishing.
-->
# SiriusMsg 0.0.1 (build 4)

Maintenance release that refreshes the bundled SwiftPython runtime with a
reliability fix.

## Changed

- Updated `SwiftPythonRuntime` to `swiftpython-commercial` `v0.5.4`, carrying the
  matched signed `SwiftPythonWorker` sidecar. This release fixes a worker-channel
  desync in the underlying IPC layer: an oversized worker response no longer
  strands bytes on the socket, so the channel recovers cleanly instead of
  repeatedly surfacing the same error. The Messages bridge, allowlist gating,
  read-only store access, send dispatch, and SwiftPython hook/adapter surface are
  unchanged.

## Verification

- App notarization: accepted by Apple notary service.
- DMG notarization: accepted by Apple notary service.
- Gatekeeper: accepted as Notarized Developer ID.
- DMG image verification: valid.
- Public bundle scan: no private developer paths, private repository owner URLs,
  credential-shaped tokens, or Python bytecode caches.

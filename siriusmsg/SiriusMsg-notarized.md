<!-- sparkle-sign-warning:
IMPORTANT: This file is signed into the Sparkle appcast. Any modifications require re-running generate_appcast or sign_update before publishing.
-->
# SiriusMsg 0.0.1 (build 3)

Maintenance release that refreshes the bundled SwiftPython runtime.

## Changed

- Updated `SwiftPythonRuntime` to `swiftpython-commercial` `v0.5.3`, carrying the
  matched signed `SwiftPythonWorker` sidecar. The Messages bridge, allowlist
  gating, read-only store access, send dispatch, and SwiftPython hook/adapter
  surface are unchanged.

## Verification

- App notarization: accepted by Apple notary service.
- DMG notarization: accepted by Apple notary service.
- Gatekeeper: accepted as Notarized Developer ID.
- DMG image verification: valid.
- Public bundle scan: no private developer paths, private repository owner URLs,
  credential-shaped tokens, or Python bytecode caches.

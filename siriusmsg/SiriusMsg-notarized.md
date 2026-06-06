<!-- sparkle-sign-warning:
IMPORTANT: This file is signed into the Sparkle appcast. Any modifications require re-running generate_appcast or sign_update before publishing.
-->
# SiriusMsg 0.0.1 (build 6)

Maintenance release that updates the bundled SwiftPython runtime used by
agent-hosted Python hooks and adapters.

## Changed

- Updated `SwiftPythonRuntime` and `SwiftPythonWorker` to
  `swiftpython-commercial` `v0.5.10`.
- Kept SwiftPython isolated to the signed `SiriusMsgAgent.app` login item; the
  outer `SiriusMsg.app` still does not load CPython at launch.
- Preserved the bundled `Python.framework` packaging path introduced in build 5.

## Verification

- App notarization: accepted by Apple notary service.
- DMG notarization: accepted by Apple notary service.
- Gatekeeper: accepted as Notarized Developer ID.
- DMG image verification: valid.
- Signed bundle verification: nested agent bundles `Python.framework`,
  `SiriusMsgHooks.framework`, and `SwiftPythonWorker` without Homebrew,
  user-home, checkout, private source, bytecode cache, or global
  `site-packages` linkage.
- Operational validation gate: passed with the notarized DMG path.

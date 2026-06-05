<!-- sparkle-sign-warning:
IMPORTANT: This file is signed into the Sparkle appcast. Any modifications require re-running generate_appcast or sign_update before publishing.
-->
# SiriusMsg 0.0.1 (build 5)

Maintenance release that fixes the signed-product Python runtime bundle so
SiriusMsg runs on a clean Mac without Homebrew Python.

## Changed

- Embedded `Python.framework` inside the bundled `SiriusMsgAgent.app` login item.
- Rewrote `SiriusMsgHooks.framework` and `SwiftPythonWorker` load commands away
  from `/opt/homebrew/opt/python@3.13` and into the nested app bundle.
- Replaced Homebrew global `site-packages` with an app-local directory and
  disabled Python bytecode writes for hosted adapters.
- Updated `SwiftPythonRuntime` and `SwiftPythonWorker` to
  `swiftpython-commercial` `v0.5.5`.

## Verification

- App notarization: accepted by Apple notary service.
- DMG notarization: accepted by Apple notary service.
- Gatekeeper: accepted as Notarized Developer ID.
- DMG image verification: valid.
- Mounted DMG payload verification: nested agent bundles `Python.framework`,
  `SiriusMsgHooks.framework`, and `SwiftPythonWorker` without Homebrew, user-home,
  checkout, private source, bytecode cache, or global `site-packages` linkage.
- Operational validation gate: passed with the notarized DMG path.
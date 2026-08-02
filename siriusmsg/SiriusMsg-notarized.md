<!-- sparkle-sign-warning:
IMPORTANT: This file is signed into the Sparkle appcast. Any modifications require re-running generate_appcast or sign_update before publishing.
-->
# SiriusMsg 0.0.1 (build 11)

Security and compatibility update for the SwiftPython adapter runtime.

## Changed

- Updated the bundled SwiftPython runtime and worker to
  `swiftpython-commercial v0.6.0-duplex.3`.
- Moved SwiftPython's proprietary runtime implementation behind its private
  Engine framework while preserving SiriusMsg's public adapter API.
- Kept the private Engine and Python runtime confined to the nested
  `SiriusMsgAgent` login item; the foreground app does not load them.

## Verification

- Swift, Python, and TypeScript test suites: passed.
- 250,000-row Messages Store WAL stress test: passed.
- Unsigned Xcode app/agent build: passed.
- Signed bundle integrity and bundled Python runtime verification: passed.
- App and DMG notarization: accepted by Apple notary service.
- Gatekeeper: accepted as Notarized Developer ID.
- DMG image, stapling, and Sparkle signature verification: passed.

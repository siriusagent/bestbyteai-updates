<!-- sparkle-sign-warning:
IMPORTANT: This file is signed into the Sparkle appcast. Any modifications require re-running generate_appcast or sign_update before publishing.
-->
# SiriusMsg 0.0.1 (build 10)

Reliability update for the app-owned bridge lifecycle, local SDK clients,
SwiftPython adapter isolation, and signed release pipeline.

## Changed

- Made Sparkle installation and login-item repair explicit and recoverable. The
  app remembers whether the bridge was running, quiesces and unregisters the
  bundled agent before installation, and consumes the restart request once
  after relaunch.
- Added typed, directly tested presentations for the menu bar, Home, Advanced,
  Adapters, Checks, About, and action feedback so the app keeps a visible
  Settings surface and reports long-running or rejected actions consistently.
- Added a minimal executable `echo_adapter.py` example. It runs inside the
  signed-agent SwiftPython boundary and returns a reply decision without
  reading `chat.db`, connecting to the service socket, or sending Apple Events.
- Expanded the local release gate to lint, format, build, and test the Python
  and TypeScript SDKs in addition to generated-artifact, Swift, Store stress,
  app, agent, entitlement, and signed-product checks.

## Fixed

- Limited Python and TypeScript subscription reconnects to transport failures.
  Authentication and other service errors now fail immediately instead of
  entering a retry loop.
- Added typed SDK attachment size and SHA-256 mismatch errors while keeping
  customer filesystem paths out of diagnostics.
- Force-respawn the exact SwiftPython worker after a handler timeout before it
  can receive more work. Registered Swift health, capability, and attachment
  callbacks remain available to the replacement worker.
- Hardened rapid service restart, send-deadline completion, durable adapter
  lease ownership, bundled login-item registration, and ScriptingBridge send
  dispatch with executable race and failure-path coverage.
- Made generated SDK installation atomic: a late schema exporter or code
  generator failure leaves all tracked artifacts unchanged.
- Replaced release-script string assertions with executable fixtures that prove
  signing, notarization, Sparkle metadata, bundled Python, SDK generation, and
  validation-artifact failures stop safely.

## Verification

- Generated SDK drift check: passed.
- Swift test suite: 343 tests passed.
- Python SDK lint, format, and 11 tests: passed.
- TypeScript SDK format, build, and 12 tests: passed.
- 12,000-row Messages Store WAL stress test: passed.
- Unsigned Xcode app/agent build: passed.
- Signed bundle integrity and bundled Python runtime verification: passed.
- App and DMG notarization: accepted by Apple notary service.
- Gatekeeper: accepted as Notarized Developer ID.
- DMG image and stapling verification: passed.
- Operational validation gate: passed with the notarized DMG path.

<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.86

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Deferred reflection no longer runs on the service worker.** Sidebar
  switch/new-chat handoff still writes the durable reflection queue on worker 0,
  but the long provider-backed reflection drain now runs on a dedicated
  reflection worker. This keeps worker 0 available for settings, channels,
  callbacks, pinned context, and other service-plane work while memory catches
  up in the background.
- **Low-memory worker pools keep chat capacity first.** Two-worker boots do not
  reserve worker 1 for reflection. Worker 1 remains the normal session worker
  and the background reflection tick skips instead of moving the stall from the
  service worker to the only chat worker.
- **Runtime role routing and tests now cover the split.** Bootstrap, respawn
  rebinds, iMessage durable turns, session selection, cron control, and
  reflection queue tests all assert the service/reflection/session worker
  contract.
- **The distributable build defaults now target alpha.86 / build 86.**

## Distribution

- Published as monotonic Sparkle build 86.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

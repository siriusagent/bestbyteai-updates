<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.13

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Improves session switch and close teardown diagnostics for worker recovery.
- Stops rendering worker no-response recovery as a native "command crash" when
  there is no crash report or Python traceback evidence.
- Records session id, worker id, PID when available, active turn id, command,
  pool state, lifecycle state, close reason/target, stream activity, and
  traceback state in worker respawn telemetry.
- Drops stale steer/pause side-channel requests as lifecycle cancellation while
  a session is closing or draining instead of submitting unnecessary eval work
  to the tearing-down worker.
- Persists Python tracebacks only when SwiftPython exposes one, and explicitly
  logs `no Python traceback captured` for supervisor-side timeout/no-response
  evidence.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

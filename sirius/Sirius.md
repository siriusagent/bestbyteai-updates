<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.52

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Session start now survives host-bridge registration races.** If the terminal
  or browser host bridge finished registering while a new session was being
  built, the active `LoopConfig` could miss the fresh callbacks and leave the
  new session attached to stale bridge topology. Session startup now snapshots
  the bridge topology epoch, releases a stale first handle when registration
  wins the race, retries once, and refuses to spin if topology changes again.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

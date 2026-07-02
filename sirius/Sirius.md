<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.107

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This release adds a sudo-style trusted-device window for channel approval
passkeys and fixes a channel-service-worker stall caused by synchronous
Keychain callbacks.

## What's new

- **Approve once, then stay trusted for a while.** After one successful
  passkey approval on a Telegram, WhatsApp, or iMessage turn, Sirius opens a
  local **trust session** for that channel+sender. While it is unexpired,
  subsequent gated tool calls on the same route short-circuit to approved with
  no relay round-trip, no channel message, and no tap — the `sudo` timestamp
  model, not `sudo -k` per call. The gate-opening approval is still
  challenge-bound WebAuthn verified locally; the relay is uninvolved in the
  window and can never widen a grant.
- **Pick how long trust lasts.** Permissions & Security → Channel Approval
  Passkey now has a trust-window picker: Off / 6h / 12h / 24h / 48h / 72h /
  1 week, defaulting to 6h. **Off** restores true per-call approval. Revoking
  or replacing the passkey clears every open session, and a new "End Trusted
  Sessions" action clears them manually.
- **Channel credential checks no longer stall the worker.** The keychain
  bridge callbacks (get/set/delete/list) are now async, and Python waits with
  a 30s timeout instead of blocking indefinitely on a synchronous host call.
  Previously, a credential status check on a messaging-channel turn could hold
  the service worker for the full 31-minute turn ceiling when the host main
  thread was busy, blocking further channel messages until the worker was
  restarted.
- **Various stability and test improvements.**

## Distribution

- Published as monotonic Sparkle build 107.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

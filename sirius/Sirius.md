<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.50

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Fresh credential reads for signed API requests.** The credential broker now
  rereads Keychain values at the execution boundary for `api_request` and
  one-shot bash/skill leases. Replacing a key in Settings no longer leaves an
  already-running worker signing with stale private-key material.
- **Kalshi contract cleanup.** Local Kalshi-style signature contracts should
  sign `{timestamp_ms}{method}{path}` and keep the private key as a companion
  secret, not as a separate HTTP contract.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

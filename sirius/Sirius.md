<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.105

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This hotfix repairs the worker-runtime passkey Settings path after alpha.104
moved enrollment calls onto the service worker but exposed that the passkey
store expected a raw SQLite connection instead of the worker's `SiriusDB`
wrapper.

## What's new

- **Passkey status now accepts the real worker DB object.** The passkey store
  now normalizes `SiriusDB` to its underlying SQLite connection, so Settings
  status/enrollment/revoke/test calls can run against the same runtime object
  used by channel workers.
- **Regression coverage for the screenshot failure.** The passkey enrollment
  API now has a Python test that calls `approval_passkey_status()` with a real
  `SiriusDB` wrapper and fails on the previous `SiriusDB.execute` error.

## Distribution

- Published as monotonic Sparkle build 105.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

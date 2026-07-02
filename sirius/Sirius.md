<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.104

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This hotfix repairs Channel approval passkey enrollment after alpha.103 fixed
the packaged WebAuthn dependency but left Settings dispatching enrollment calls
outside the bound Sirius worker runtime.

## What's new

- **Passkey enrollment now uses the service worker runtime.** The Permissions
  & Security passkey status, enrollment, revoke, and test actions now dispatch
  through the worker-bound Sirius runtime instead of the main SwiftPython
  interpreter, so the Python enrollment API can access the live `SiriusDB` and
  `PersistentConfig`.
- **Core runtime readiness checks include WebAuthn.** The core runtime health
  check now requires both `fido2` and the Sirius WebAuthn module before treating
  the installed runtime as ready.

## Distribution

- Published as monotonic Sparkle build 104.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

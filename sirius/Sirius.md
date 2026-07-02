<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.103

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This hotfix repairs Channel approval passkey enrollment for users who install
Sirius through the signed update runtime.

## What's new

- **Passkey enrollment dependencies ship with the runtime.** The signed core
  Python runtime now includes the WebAuthn `fido2` library required by the
  Channel approval passkey setup flow, so users do not need to install Python
  packages manually.

## Distribution

- Published as monotonic Sparkle build 103.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

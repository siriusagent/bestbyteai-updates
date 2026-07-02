<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.106

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This hotfix repairs Channel approval passkey enrollment after Safari reached
the live enrollment page but rejected the WebAuthn creation options because the
challenge was serialized under the wrong key shape.

## What's new

- **Safari passkey enrollment receives valid WebAuthn JSON.** Sirius now
  preserves the `fido2` library's browser-facing `publicKey` option shape when
  creating enrollment requests, including the required `challenge` string.
- **Regression coverage for the relay payload.** The WebAuthn service and
  Settings enrollment bridge tests now assert that enrollment options are
  parseable as `PublicKeyCredentialCreationOptionsJSON`.

## Distribution

- Published as monotonic Sparkle build 106.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

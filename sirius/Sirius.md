<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.49

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Credential companion setup.** The Credentials settings pane now makes
  referenced companion contracts actionable: missing companions show **Create**
  and open a prefilled private-key contract draft, while existing companions
  show **Open** and select the contract instead of silently doing nothing.
- **Signed API request contracts.** Signature auth defaults now generate the
  key, timestamp, and signature header templates from the declared key header
  name. Kalshi-style contracts default to `KALSHI-ACCESS-KEY`,
  `KALSHI-ACCESS-TIMESTAMP`, and `KALSHI-ACCESS-SIGNATURE`.
- **Signer compatibility.** The broker accepts both hyphenated and underscored
  signature algorithm names, so UI-authored `rsa-pss-sha256` contracts execute
  through `api_request` instead of failing at signing time.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.51

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Permission preset changes no longer break local credential contracts.**
  Switching the permission preset (or refreshing wallet/MCP permission state)
  mid-session rebuilt the permission context without the live credential
  broker, so `credential_request` denied user-defined credential contracts
  with `unknown_requirement` even though `credential_status` showed them as
  available. Every permission-context rebuild path now re-stamps the live
  broker state, so locally declared contracts (e.g. Kalshi-style signature
  contracts) stay requestable for the whole session.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

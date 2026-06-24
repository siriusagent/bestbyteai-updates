<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.80

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Generic programmatic HTTP signers for credentials.** The `api_request`
  credential broker gains a first-class, provider-neutral `signer:<id>` auth
  path alongside the existing `Header` / `Bearer` / `Query` / `Basic` /
  `Signature` schemes, for request-derived auth that cannot be expressed as
  static injection or declarative canonical-string signing (JWT/JWS,
  request-bound tokens, nonce/multi-secret schemes).
  - A contract may carry an opaque `http_signer` config table, preserved
    verbatim across config, the secret-free catalog, and the UI.
  - Ships one built-in generic signer, **`jwt_bearer`**, producing verifiable
    compact JWS for **ES256**, **EdDSA**, and **RS256** — built on the existing
    `cryptography` dependency (no new PyJWT dependency).
  - **Fails closed:** an unregistered `signer:<id>` or invalid signer config
    returns a structured error *before* any grant is minted or request is
    sent — Sirius never silently sends an unsigned request.
  - Signers read only the primary secret and declared companions
    (`key_id_requirement = "primary"` selects the primary); generated tokens and
    signing keys are never logged, returned, or previewed.
  - No provider names, presets, URLs, or claims are baked into the generic core.
- **New Signer editor in Credentials settings.** The HTTP Request Contract
  picker adds a `Signer` option with a Signer ID field, a JSON config editor
  with live validation, and a token-free request preview that shows the derived
  auth line and companion requirement IDs. Signer config is JSON in the UI and
  TOML on disk.
- **The distributable build defaults now target alpha.80 / build 80.**

## Distribution

- Published as monotonic Sparkle build 80.
- Ships a refreshed signed core-runtime feed for the programmatic-signer engine
  and credential-broker changes.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

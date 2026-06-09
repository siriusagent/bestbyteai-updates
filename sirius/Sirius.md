<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.36

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixes a provider-auth failure where the active session could report
  `API 401: You didn't provide an API key` even though the OpenAI key existed
  in Keychain and the provider probe passed. Sirius now repairs drift between
  the flat active-provider fields and the provider library, preserves the key
  reference in live provider swaps, and keeps OAuth rows from being rewritten as
  API-key rows.
- Improves Report Bug provider diagnostics with a sanitized auth-method fact so
  future provider/keychain mismatches show the actual auth path without
  including secret values.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

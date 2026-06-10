<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.43

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixed a provider-auth regression where a respawned worker could replay a
  stale OpenAI API-key snapshot after the app had already saved a ChatGPT OAuth
  configuration, surfacing `OpenAICompatibleProvider` HTTP 401 errors with no
  API key.
- Worker runtime rebinds now reload current provider config and prefetched
  credentials at respawn time instead of using boot-time JSON.
- Added an engine-side guard that routes stale OpenAI API-key snapshots through
  the ChatGPT OAuth provider when the API-key secret is absent but the OAuth
  credential is present.
- Carries alpha.42 fixes forward, including shipped browser camera entitlement,
  media privacy declarations, signed-bundle media checks, and no-camera/no-mic
  diagnostics in Permissions & Security.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

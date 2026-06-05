<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.5

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Fixes

- Prevents low-memory installs from implicitly loading the local
  sentence-transformers embedding model during startup/backfill unless explicitly
  configured with `SIRIUS_MEMORY_EMBEDDING_BACKEND=local`.
- Pins production Python worker BLAS threads to one to reduce native library
  overcommit during early worker boot.
- Stops channel event polling once SwiftPython reports the pinned service worker
  is permanently dead, instead of repeatedly submitting drain work to the dead
  worker.
- Ships as build `5`, allowing Sparkle to update alpha.4/build `4` installs.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key and update feed are enabled for alpha update testing.

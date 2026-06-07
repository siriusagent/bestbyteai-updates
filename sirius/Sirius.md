<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.20

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixes Help -> Report Bug AI generation when the app host has updated before
  the installed core runtime component. Sirius now detects the stale-runtime
  `generate_bug_report` missing-function error, installs a worker-local
  compatibility shim, and retries the normal report-generation call once.
- Keeps unrelated AI/provider failures visible instead of masking them as
  compatibility problems.
- Narrows the compatibility patch to the service worker that is generating the
  report; active session workers are not touched.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

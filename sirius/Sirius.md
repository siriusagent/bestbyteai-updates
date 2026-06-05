<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.6

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Adds the first-run Sirius Setup flow with welcome, SwiftPython, capabilities,
  license acceptance, core-runtime install verification, and launch gating.
- Requires license acceptance before the agent runtime is installed or started.
- Moves the core agent runtime out of the public app bundle and into a signed
  runtime feed hosted under the Sirius update channel.
- Builds the public signed product without a bundled `sirius_agent` runtime
  seed, reducing what can be copied from the public DMG.
- Keeps optional heavy components installable outside the signed app bundle.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key and update feed are enabled for alpha update testing.

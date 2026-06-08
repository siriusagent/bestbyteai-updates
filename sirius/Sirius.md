<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.30

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixes the Ollama Compatible Model Hub failure in alpha.29 where the Settings
  pane called the Python hub bridge with six positional arguments even though
  the installed runtime accepts search, cursor, and sort as keyword-only
  paging arguments.
- Adds regression coverage for the bridge contract so future Swift changes
  reject the exact positional call shape that produced the public
  `compatible_model_hub_json() takes from 0 to 3 positional arguments but 6
  were given` error.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

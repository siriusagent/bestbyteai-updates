<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.12

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Removes runtime component install paths from first-run setup and the
  Components settings tab.
- Rewrites Components settings copy so required and optional components are
  described by product capability instead of internal runtime layout.
- Keeps install state and component actions unchanged while tightening tests so
  user-facing component surfaces do not reintroduce path breadcrumbs.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

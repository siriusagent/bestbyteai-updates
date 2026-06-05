<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.3

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Fixes

- Fixes an installed-app OAuth callback crash caused by a trapping SwiftPM
  resource-bundle lookup for the success-page icon.
- Keeps the OAuth success page resilient if its decorative icon cannot be
  loaded.
- Ships as build `3`, allowing Sparkle to update alpha.2/build `2` installs.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key and update feed are enabled for alpha update testing.

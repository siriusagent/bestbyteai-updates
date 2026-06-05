<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.4

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Fixes

- Fixes an installed-app crash when installing terminal shell integration from
  Settings.
- Removes trapping SwiftPM resource-bundle lookups from runtime SiriusUI
  resource paths used by terminal, Mind, DiffTree, and OAuth callback surfaces.
- Ships as build `4`, allowing Sparkle to update alpha.3/build `3` installs.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key and update feed are enabled for alpha update testing.

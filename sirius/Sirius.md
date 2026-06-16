<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.67

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Fixes

- **Telegram bridge replies use the stable plain-send path again.** Automatic
  Telegram replies no longer depend on Telegram's rich-message endpoint.
- **Rich Telegram sending remains explicit.** The dedicated rich Telegram
  command is still available for direct sends and advanced Telegram fields,
  but normal bridge replies stay on the ordinary bot-message path.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.60

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Telegram can send native rich messages.** Agents can now use
  `telegram_send_rich` to send Bot API `InputRichMessage` content with either
  `html` or `markdown`, plus Telegram's `is_rtl` and
  `skip_entity_detection` flags.
- **Telegram rich sends are terminal channel actions.** After
  `telegram_send_rich` delivers a message, the turn ends with no bridge
  auto-send, preventing a second plain-text reply.
- **Telegram chat IDs match the Bot API contract.** Telegram outbound sends
  accept numeric chat IDs and `@username` targets.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

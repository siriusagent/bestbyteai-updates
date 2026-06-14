<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.61

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Telegram rich sends now render inline in Sirius.** `telegram_send_rich`
  appears as the same quiet paper-plane transcript annotation used by channel
  sends, not as a generic full-width tool card.
- **Telegram rich messages follow Bot API 10.1.** The Telegram rich-send tool
  now teaches and passes through native rich Markdown tables, rich HTML tables,
  headings, lists, quotes, footnotes, formulas, media/details blocks, and the
  full documented `sendRichMessage` optional parameter set.
- **Rich-send details stay compact.** Sirius transcript details show the
  delivered Telegram route plus relevant rich-message options without exposing
  raw transport JSON as the primary UI.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

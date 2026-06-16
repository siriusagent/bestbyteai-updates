<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.66

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Channel settings now hot-swap without restarting Sirius.** Enabling or
  configuring Telegram, Discord, WhatsApp, SMS/MMS, Google Chat, IRC, or
  iMessage now refreshes the live runtime workers and sidebar state instead of
  requiring a full app restart.
- **Telegram replies use rich formatting automatically.** Normal Telegram
  channel replies now use rich Markdown when the provider supports it, with a
  plain-text fallback for delivery safety. The dedicated rich Telegram command
  remains available for direct sends and advanced Telegram fields.
- **SiriusMarkdown is updated to 0.5.10.** The app bundle resolves the current
  public renderer package for transcript, plan, and Markdown preview surfaces,
  including chat-style LaTeX recovery for single-line display math and common
  bare TeX commands in assistant prose.
- **Channel runtime installs are repaired for fresh machines.** Fresh installs
  and repaired runtimes include the provider packages needed for the Channels
  settings pane and webhook-backed transports.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

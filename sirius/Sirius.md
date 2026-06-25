<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.81

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Rich, automatic native reply delivery across channels.** Channel providers
  gain a `send_assistant_reply` path so assistant responses are delivered in
  each platform's structured/rich format (embeds where supported) instead of
  flattened plain text.
  - `ChannelManager` now routes replies through a unified `send_auto` that
    prefers the rich format and **falls back to plain text** when a provider or
    payload cannot carry it.
  - A new `ChannelDeliveryFailedEvent` captures and logs delivery failures so
    bridge errors are observable rather than silent.
  - Discord, Google Chat, WhatsApp, Telegram, and SMS providers were aligned to
    the new reply mechanism for consistent behavior across platforms.
- **Assistant message overflow menu.** Finalized assistant rows in the
  transcript now expose an overflow menu with **Reply to** and **Research on
  web** actions.
  - "Reply to" carries quoted context into the composer and persists a UI-only
    reply reference so the quoted thread survives across sessions.
  - A new `reply_reference_json` column on the messages store records the reply
    metadata; `TranscriptStore` and `SessionPersistence` were updated to read
    and write it.
- **The distributable build defaults now target alpha.81 / build 81.**

## Distribution

- Published as monotonic Sparkle build 81.
- Ships a refreshed signed core-runtime feed for the channel-delivery and
  assistant-reply engine changes.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

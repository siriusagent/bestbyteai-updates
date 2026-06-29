<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.93

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Channel replies are now delivered through a durable outbox.** A new
  `channel_outbox` table persists completed assistant turns for
  provider-backed channels so transient transport failures are retried
  automatically instead of dropping the reply. `ChannelBridge` and
  `ChannelHost` integrate the outbox for automatic reply delivery, and
  delivery outcomes are logged with richer error context for debugging.
- **In-session commands `/model`, `/provider`, and `/retry` are available.**
  Sessions can switch model or provider mid-conversation and regenerate the
  last user request without restarting the turn.
- **Capable channels now render live turn progress.** A `ChannelProgressRenderer`
  drives typing indicators and evolving status cards while a message is being
  processed. Telegram, Discord, Google Chat, and WhatsApp declare optional
  support for `typing_indicator` and `edit_message`, with new env vars tuning
  channel turn liveness and progress rendering.
- **Native reply delivery is hardened with diagnostics.** `ChannelManager.send_auto`
  retries transient transport failures when delivering native replies, and
  `ChannelSentEvent` / `ChannelDeliveryFailedEvent` now carry
  `native_attempted`, `native_surface`, `native_attempt_count`, and
  `fallback_reason`, persisted into the `channel_outbox` schema for delivery
  tracking.
- **New session and repository management commands.** `sirius init [PATH]`
  bootstraps or backfills a repository, and `sirius session` gains
  `export SESSION_ID` (Markdown or JSON), `rename SESSION_ID TITLE`, and
  `remove SESSION_ID`. The in-session `/export` command exports the current
  transcript.
- **The bundled Python core runtime refreshes with this build.** The signed
  core-runtime feed ships the latest `sirius_agent` package, including the
  durable outbox, progress rendering, and native delivery diagnostics from
  this cycle.
- **The distributable build defaults now target alpha.93 / build 93.**

## Distribution

- Published as monotonic Sparkle build 93.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

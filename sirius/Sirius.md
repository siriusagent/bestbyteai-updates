<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.95

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This is a **hotfix** over alpha.94. It stops the channel progress status card
from preempting provider-native final replies.

## Changes

- **Progress cards no longer swallow native final replies.** On edit-capable
  channels (Telegram, Discord, Google Chat) the evolving status card was
  always edited into the final answer, which preempted the provider-native
  final surface (`send_assistant_reply`). The card is now deleted before the
  final send when `ChannelManager.would_attempt_native_reply` is true for the
  rendered reply, so `deliver_assistant_reply` can route through the native
  path with plain fallback. Edit-only / plain delivery still resolves the
  card into the final answer.
- **New native-reply predicate.** `ChannelManager.would_attempt_native_reply`
  exposes the same shape gate `send_auto` uses (callable
  `send_assistant_reply` + `native_reply_applicable`), so the bridge can
  decide card-vs-native without duplicating the delivery rules. The shared
  `_native_reply_applicable` helper now backs both `send_auto` and the
  predicate.
- **Single-delivery guarantee preserved.** The status card is either
  edited-into-final or deleted-then-final; `deliver_assistant_reply` and the
  outbox still fire exactly once per turn, never both.
- **The bundled Python core runtime refreshes with this build.** The signed
  core-runtime feed ships the updated `sirius_agent` package, including the
  channel progress / native reply delivery fix from this hotfix.
- **The distributable build defaults now target alpha.95 / build 95.**

## Distribution

- Published as monotonic Sparkle build 95.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

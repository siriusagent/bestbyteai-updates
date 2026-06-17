<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.70

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Fixes

- **Recall tool loops recover before flooding transcripts.** Repeated
  no-progress memory, session-search, and tool-search calls now enter the
  cycle-recovery lane after four consecutive recall attempts.
- **Manual steers take the next turn before background wakeups.** Queued manual
  steers are requeued before background events or goal continuations when a
  turn ends idle, avoiding stuck "sent" steers.
- **Telegram channel chats opened in Sirius can reply again.** Messages sent
  from a Telegram-backed chat in the Sirius sidebar use the live channel
  transport instead of failing with an unknown rich-send command.
- **Provider-limit failures are clearer in channels.** When the selected model
  or provider rejects a channel turn because of usage limits or credentials,
  Sirius tells the channel user what failed instead of sending the generic
  retry message.

## Distribution

- Published as monotonic Sparkle build 70.
- Ships a refreshed signed core-runtime feed for the memory-loop guard.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

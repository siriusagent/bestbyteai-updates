<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.69

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Fixes

- **Telegram channel chats opened in Sirius can reply again.** Messages sent
  from a Telegram-backed chat in the Sirius sidebar now use the live channel
  transport instead of failing with an unknown rich-send command.
- **Provider-limit failures are clearer in channels.** When the selected model
  or provider rejects a channel turn because of usage limits or credentials,
  Sirius now tells the channel user what failed instead of sending the generic
  retry message.

## Distribution

- Published as monotonic Sparkle build 69 so installed alpha users receive the
  channel fix through auto-update.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

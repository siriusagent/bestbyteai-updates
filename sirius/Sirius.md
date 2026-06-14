<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.59

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Telegram channel replies no longer fail when the agent uses the current
  chat display name.** Channel-backed sessions now carry the real inbound
  platform and channel id into `channel_send`, so the tool sends to the active
  route instead of trying to parse a display name as a numeric Telegram id.
- **Channel-send errors render as readable messages.** The transcript and tool
  popovers now show the relevant error text instead of raw JSON envelopes.
- **Empty background-status polling is suppressed.** `bash_status` is visible
  only when background tasks or queued background events can advance the turn,
  preventing no-progress status polling loops.
- **Release builds resolve against SiriusMarkdown 0.5.8.**

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

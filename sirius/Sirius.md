<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.102

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This release introduces a new way to approve your agent's actions from your
phone, plus a couple of correctness fixes for messaging-channel sessions.

## What's new

- **Approve agent actions from your phone with Face ID / Touch ID.** When an
  agent hits a permission gate during a Telegram, WhatsApp, or iMessage turn,
  Sirius now sends an approval link to that channel. Tap it, confirm a short
  human-readable code, and approve or deny with a platform passkey — no laptop
  required. A new **Channel approval passkey** section in Permissions &
  Security lets you enroll, replace, or revoke the passkey used to authorize
  these requests, and send yourself a test approval to confirm the path works.
- **Per-turn provider avatars stick in channel transcripts.** Assistant
  replies in messaging-channel sessions now show the correct provider avatar
  on each turn instead of falling back to the foreground window's provider.
- **Opening Sirius from an approval or settings link now lands you in the
  right place.** Links that use the Sirius app scheme route directly to the
  relevant Settings section (e.g. setting up your approval passkey) instead
  of dropping you at the default view.
- **Approval throughput and timeout handling are more robust** under rapid
  or overlapping requests, so a burst of approvals won't trip over itself.
- **Various stability and test improvements.**

## Distribution

- Published as monotonic Sparkle build 102.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

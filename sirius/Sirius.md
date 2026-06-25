<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.82

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Fix channel session routing (BUG-273).** The persisted `channel_sessions`
  mapping is now authoritative before a cached `ChannelBridge` `AgentLoop` is
  reused. When the database mapping for a provider/sender is missing or has
  changed, Sirius drops the stale cached loop, clears its last-active marker,
  and creates or resumes the session described by SQLite instead of appending
  to the old in-memory session id. This prevents a deleted (e.g. Telegram)
  mapping from resurrecting the previous session row as a plain
  `source=sirius` session.
- **Fix visible refresh after a channel turn.** Selected-channel transcript
  refresh now reuses the existing desktop session-open primitives:
  `refreshAfterChannelTurn` reloads sidebar metadata for every completion,
  ignores unselected sessions, and refreshes the selected channel conversation
  through `switchToSession` (when idle) or `viewSessionAsHistorical` (while the
  controller is running/cancelling). The channel-only direct transcript reload
  helper is removed, so channel sends no longer require clicking away and back
  to pick up the reply.
- **The distributable build defaults now target alpha.82 / build 82.**

## Distribution

- Published as monotonic Sparkle build 82.
- Ships a refreshed signed core-runtime feed for the channel-bridge routing fix.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

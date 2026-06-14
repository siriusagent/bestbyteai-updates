<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.58

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Right-panel Agent terminal and Browser updates are visible again after
  bridge topology refreshes.** Session-tagged terminal and browser callbacks
  now resolve the active session's visible right-panel coordinators instead of
  falling back to a stale/offscreen coordinator. This covers Agent PTY command
  output, browser-use actions, and rendered `web_search` / `web_read` captures.
- **DiffTree folder dirty-count badges no longer blank during fast refresh.**
  The phase-1 filesystem navigator now preserves same-workspace dirty
  decorations from the last promoted Git snapshot while the phase-2 Git status
  promotion is still running.
- **Background-events UI mockup is included for the current design handoff.**
  The mockup records the existing watch/status surfaces without changing the
  shipped app chrome.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

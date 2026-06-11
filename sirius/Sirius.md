<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.48

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Background task events.** `bash` and `bash_status` now support `notify_on`
  watches for tracked background jobs. Sirius scans appended task output
  off-LLM, records matching evidence lines, wakes idle sessions, and injects
  background event evidence into the next turn instead of forcing agents to
  hand-roll polling loops.
- **Watch-aware goal continuation.** Armed background watches stretch the goal
  continuation timer and the blind background-attention poll, while real
  events wake the session promptly. `goal(action="complete")` now reports
  still-running background tasks so monitors are not orphaned silently.
- **Background-event lifecycle hardening.** Watch debounce buffers persist
  across worker respawn, event sinks are session-owned, closing a session clears
  only its own sink, and Swift reads the documented watch/wake debounce env
  vars.
- **Watch-aware transcript and status UI.** Bash cards show a watch chip, tool
  annotations summarize watched tasks and event counts, background events render
  as quiet evidence annotations, and the goal status popover reflects active
  watched tasks.
- **Credential contract editor.** Credentials settings now exposes the full
  local contract model for user-owned credentials, including audience,
  provider, auth scheme, scopes, environment aliases, and provider-specific
  auth fields. Built-in catalog contracts remain read-only.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

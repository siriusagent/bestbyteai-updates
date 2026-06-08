<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.31

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Adds opt-in MCP tool classification on each server sheet. When enabled,
  Sirius classifies discovered tool names, descriptions, and schemas once after
  `tools/list`, stores profiles by SHA-256 of canonical tool metadata, and lets
  Permissions & Security regulate future calls. Leaving it unchecked preserves
  the previous MCP behavior.
- Hardens classified MCP enforcement before tool dispatch, including nested
  `execute_dag` child calls. High-risk classified calls cannot be silently
  allowed by stale profiles, and economic submit actions fall back to exact-call
  approval when a server-specific idempotency adapter is not available.
- Fixes live MCP settings reload so removed or restarted servers unregister
  stale tools/profiles and keep per-server permission presets in sync.
- Fixes Goal mode settings propagation. Saved token limits, hard ceilings, and
  auto-extend settings hot-apply to live session workers and update the worker
  respawn start arguments, so newly created goals no longer fall back to code
  defaults.
- Fixes sidebar auto-title generation. The title path falls back from the
  auxiliary provider to the primary provider, then to a deterministic local
  title, and the Swift host applies generated titles to the correct session row
  immediately even if selection changes while generation is running.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

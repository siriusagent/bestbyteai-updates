<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.40

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixes Gemini provider switches from Codex-backed conversations. Codex
  encrypted reasoning state is now kept out of Gemini `thoughtSignature`
  replay, avoiding Gemini's `TYPE_BYTES` base64 decode rejection.
- Updates SiriusMarkdown to `0.5.6`, which keeps transcript/document selection
  indexing duplicate-tolerant and preserves clickable links in prepared
  Markdown lines.
- Carries the alpha.39 fixes forward: goal-mode continuation hardening,
  safer provider document projection, MCP classification/preflight updates,
  Report Bug evidence bundles, interruptible tool execution, wallet checkout
  constraints, dynamic UI rendering hardening, and signed Sparkle/core-runtime
  update metadata.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

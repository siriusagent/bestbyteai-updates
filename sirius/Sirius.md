<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.47

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **`api_request` — broker-mediated authenticated HTTP tool.** Models can now
  make authenticated API calls against any declared credential contract without
  ever seeing secrets. The broker resolves credentials, applies the auth scheme
  (bearer, header, query, basic, or a fully declarative signature spec), and
  redacts responses. Host-pinned, HTTPS-only, no redirects. GET/HEAD ride an
  existing grant; mutating methods re-prompt every call.
- **CLI sub-agents.** Any coding-agent CLI (Codex CLI, Claude Code, Gemini CLI,
  or arbitrary binaries) is now dispatchable via `subagent_dispatch`. One-click
  install in Agent & Subagents settings, live detection, and auto-enable on
  success.
- **Sub-agent answers read inline in the transcript.** Delegated reports flow
  with the prose instead of being buried in a card body.
- Fixes Gemini provider switching replaying Codex encrypted reasoning as a
  Gemini `thoughtSignature`.
- Fixes stale OpenAI API-key snapshots creating keyless public providers when
  ChatGPT OAuth is present; respawned workers now reload current config.
- Fixes goal mode letting narration-only turns silently end autonomous
  continuation while the goal stayed active.
- Fixes Anthropic document attachments failing for non-PDF attachments.
- Carries all alpha.46 fixes forward.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

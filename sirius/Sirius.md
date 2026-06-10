<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.41

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Added CLI sub-agents. Codex CLI, Claude Code, Gemini CLI, and custom CLI
  agents can now be dispatched through `subagent_dispatch`; each CLI keeps its
  own loop, login, tools, and sandbox while Sirius sends the task over stdin
  and reads the final answer back.
- Added a CLI Agents group in Agent & Subagents settings with install
  detection, version/auth badges, one-click npm install, Terminal-based sign-in,
  enable/disable controls, portable TOML config, and live session reload after
  toggles.
- Made sub-agent dispatch more resilient: parent timeouts now call any
  agent-provided `cancel()` method, CLI subprocesses are killed on timeout, and
  CLI-advertised timeouts can raise the parent dispatch budget without lowering
  the global default.
- Improved transcript narration for sub-agents. Dispatch rows now read as
  `Dispatched <agent> ...`, show agent/task/status/elapsed details, and promote
  the child agent's markdown answer inline beneath the annotation instead of
  hiding it in the tool popover.
- Carries alpha.40 fixes forward, including Gemini provider-switch reasoning
  cleanup and the SiriusMarkdown 0.5.6 transcript/link-selection update.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

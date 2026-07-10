<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.113

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This release ships the accumulated in-flight work since alpha.112: dynamic
reasoning controls, provider/model-discovery hardening, automation permission
improvements, transcript and composer fixes, session shutdown cleanup, DiffTree
Markdown preview sizing, and SiriusMarkdown 0.6.7.

## What's new

- **Dynamic reasoning effort controls.** Provider model discovery now carries
  reasoning-capability metadata through config, SettingsBridge, hot-swap, and
  the composer model pill. Supported OpenAI-compatible/Codex/Anthropic models
  can expose effort controls without forcing unsupported providers into invalid
  request payloads.
- **Model discovery and provider failure handling are tighter.** The runtime
  keeps capability defaults out of persistent config, improves direct-provider
  parity, and carries clearer recovery state when provider swaps or discovery
  calls fail.
- **Context & Memory embedding credentials are routed more carefully.** OpenAI
  embeddings now prefer a Platform API key and reject ChatGPT OAuth-style
  bearer tokens for `api.openai.com`, avoiding repeated unauthorized embedding
  backfill attempts.
- **macOS automation permissions are more precise.** Action-scoped authority
  updates and remembered approval handling reduce unnecessary prompts while
  keeping command approvals tied to the intended automation surface.
- **Composer rich paste no longer sticks after send.** Rich paste state is
  normalized after message submission so the next draft starts cleanly.
- **Session shutdown paths are cleaner.** Session close and runtime teardown
  now resolve worker-bridge shutdown paths more explicitly, including sandbox
  runtime cleanup.
- **DiffTree Markdown Preview keeps the right-panel width contract.** Markdown
  preview rendering is constrained to the visible panel rather than leaking
  package-owned document overflow into the shell.
- **SiriusMarkdown 0.6.7.** The app bundle picks up the compiler-portable
  SiriusMarkdown 0.6.7 release, including the 0.6.6 block-style API,
  GitHub-inspired preset, atomic inline attachments, expanded native math
  corpus, cache correctness, serializer, and concurrency hardening.
- **Transcript tail-smoothness groundwork is documented and partially staged.**
  The release includes the current plan/runbook updates and isolated runner
  tooling for streaming-tail verification.

## Notes

- **Sparkle build version** is `113` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on `112` or earlier will offer this
  build.
- This build includes Python runtime input changes since alpha.112, so the
  signed core-runtime feed is refreshed with the same `0.1.0-alpha.113`
  version.

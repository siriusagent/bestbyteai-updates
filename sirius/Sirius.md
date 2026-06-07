<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.22

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Replaces the generic Help -> Report Bug log bundle with a category-scoped
  diagnostics flow that mirrors Settings, including Freeform.
- Adds recommended and optional checks for Network & Providers, Credentials,
  GitHub, Channels, Wallets, Context/Cron, MCP/Tools/Skills, and
  Permissions/Security.
- Collects deterministic, sanitized facts only: provider shape without secrets,
  credential presence booleans, GitHub auth/capability status, channel and
  wallet status, context/cron health, MCP/tool/skill counts, and selected
  security settings.
- Writes both `diagnostics.json` and readable `report.md` into the private local
  bundle, with failed collectors recorded as `collector_failed` facts.
- Keeps `/usr/bin/sample` as an explicit opt-in check and keeps full local
  bundles private unless the user chooses to share them.
- Fixes report markdown rendering so generated multiline text does not show
  JSON-escaped `\n`.
- Avoids malformed GitHub issue URLs by copying a concise sanitized body and
  opening a title-only issue draft.
- Verifies the packaged runtime and signed runtime feed include
  `sirius_agent/providers/ollama_registry.json`, so installed builds can prove
  local Ollama registry availability without a source checkout.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

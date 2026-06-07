<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.24

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixes Knowledge base rebuild/backfill actions that could show
  `run_knowledge_ingest_now: no runtime bound for this worker` when the
  service-worker control plane needed to rebind a session runtime.
- Fixes Report Bug -> MCP, Tools & Skills diagnostics when collection runs on
  the service-worker control plane without a live session registry.
- Reports the MCP SDK package version even when the SDK module lacks
  `__version__`.
- Reports deterministic default tool and skill counts instead of `0` when no
  session registry is attached.
- Adds bounded per-MCP-server enabled, probe-code, tool-count, resource-count,
  and prompt-count facts without exposing server command, env, header, or secret
  configuration.
- Fixes installed-app subprocess PATH resolution for user tools such as `npx`,
  `uvx`, `rg`, `gh`, and editor CLIs while keeping Sirius's embedded Python
  import environment out of child processes.
- Replaces the static Ollama registry with a Sirius-owned Compatible Model Hub
  that discovers current HF GGUF candidates for the local machine, ranks by
  machine fit before popularity, imports through Sirius model storage, and
  reports model-root provenance in diagnostics. Sirius does not ship a curated
  model list in this build.
- Clarifies that optional Python packages for MCP servers, tools, skills, and
  integration extras are installed from Settings -> MCP, Tools & Skills ->
  Components, not by modifying the sealed app bundle.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

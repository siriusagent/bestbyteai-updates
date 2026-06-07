<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.25

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Removes the packaged knowledge-base runtime/wiki source path from the
  Context & Memory settings UI. The Knowledge base card now shows counts and
  actions only, without exposing the app's internal runtime layout.
- Includes the alpha.24 Knowledge base runtime rebind fix for
  `run_knowledge_ingest_now: no runtime bound for this worker`.
- Includes the alpha.24 Compatible Model Hub work: no curated static Ollama
  list, HF GGUF discovery for the local machine, fit-first ranking, Sirius
  model storage, and diagnostics provenance.
- Clarifies that optional Python packages for MCP servers, tools, skills, and
  integration extras are installed from Settings -> MCP, Tools & Skills ->
  Components, not by modifying the sealed app bundle.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

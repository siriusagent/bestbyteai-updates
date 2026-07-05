<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.108

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This release adds local GGUF model import to the Ollama admin, hardens the
session graph and persistence layer, and picks up the SiriusMarkdown 0.6.0
transcript rendering improvements.

## What's new

- **Import local GGUF models into Ollama.** The Ollama admin now exposes
  Ollama's blob-backed create API, so you can point Sirius at a `.gguf` file on
  disk and register it as a model without a manual Modelfile round-trip. The
  Compatible Model Hub flow continues to work unchanged; the new path is for
  bringing your own weights. The Network & Providers diagnostics still report
  `~/.sirius/models` roots and provenance counts so DMG-installed builds can
  prove the hub is present without a source checkout.
- **Tighter session graph and DB layer.** The session graph, project, and DB
  modules were refactored to clear `basedpyright` `Any` drift and break mutual
  import cycles. Two new stdlib-only dependency leaves
  (`sirius_agent/db_protocol.py` and `sirius_agent/memory/session_graph_paths.py`)
  now sit under the persistence stack, and SQLite operations flow through typed
  helpers. No user-facing schema change; this is structural hardening that
  keeps the type checker clean and the dependency graph acyclic.
- **SiriusMarkdown 0.6.0.** The transcript renderer picks up the streaming
  performance rework (CTLine creation moved into the prepare phase, incremental
  snapshot publishing via `MarkdownPreparedSnapshotDiff`, cached selection
  fragment geometry), cross-block selection consistency for table cells, list
  items, code, math, and HTML blocks, and native math rendering improvements
  (real ascent/descent from `MTMathList`, screen-backed rasterization scale,
  hardened `\begin{...}` streaming detection).
- **Various stability and test improvements.**

## Distribution

- Published as monotonic Sparkle build 108.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing. This build ships a refreshed signed core
  runtime because the Sirius Python package inputs changed since alpha.107.

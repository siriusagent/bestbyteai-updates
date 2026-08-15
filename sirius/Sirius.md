<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.023

Alpha.023 makes Sirius's memory retrieval visible and user-controlled, replaces
the heavyweight local-embedding stack with a managed native runtime, and gives
the browser first-class tab, link, and site-identity controls.

## Embeddings and memory

- **Choose where semantic recall runs.** Context & Memory now offers On this
  Mac, an explicitly selected cloud provider, or Off for keyword and graph
  recall only. Source, model, privacy destination, health, and index state stay
  visible together.
- **Inspect the production recall path.** Search saved knowledge across memory,
  profile, and references; examine ranked Meaning, Wording, and Connections
  evidence; and compare an active index with a ready candidate. Inspection does
  not save the query or update memory-access metadata.
- **Switch without risking the working index.** Sirius builds and validates a
  candidate generation before activation, catches up intervening writes, and
  retains explicit retry, cancellation, rollback, and Off-mode paths.
- **Run local embeddings through a managed native component.** One bounded
  app-lifetime service supplies every worker from a signed llama.cpp engine and
  pinned GGUF model. Model bytes remain outside the app, and the supported path
  installs no Torch, Transformers, sentence-transformers, or remote model code.

## Browser

- Tabs display bounded declared favicons with a safe site fallback.
- Native tab actions include pinning, duplication, directional and other-tab
  closing, plus moving the live tab into a new Sirius window without reloading
  it or breaking Browser Use identity.
- Link menus can open in a new tab, Sirius window, or default browser; download
  directly or with a chosen destination; and add the link to Safari Reading
  List while preserving applicable WebKit system actions.

## Compatible Model Hub

- Search no longer hides new GGUF text architectures behind a Sirius-maintained
  allowlist; the installed Ollama daemon remains the compatibility authority.
- Paging and capability filtering stay usable on large result sets. Import now
  checks peak space on each affected volume, pins the discovered repository
  revision, removes redundant staging bytes after success, and records
  installation only after Ollama creates the model tag.

## Privacy and reliability

- Existing installations pin their previously effective embedding backend
  without issuing a model request. Cloud memory and reference text is sent only
  after an explicit persisted cloud-source choice.
- Embedding cache keys include immutable model identity and semantic role.
  Token-aware chunking reserves special-token headroom, local-process recovery
  checks real health, and warm requests avoid repeatedly hashing model files.

## Verification

- The non-slow engine gate passed 7,807 tests with 17 skips and 13
  deselections. The generated wiki passed its exact drift audit.
- The native source suite passed 3,365 XCTest cases plus all 13 Swift Testing
  cases, with 20 skips and zero failures.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 148 with the matching signed core-runtime feed.

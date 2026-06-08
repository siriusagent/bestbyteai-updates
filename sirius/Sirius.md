<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.29

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixes Apple Mail replies that could be sent with an empty body. Sirius now
  validates reply content before save/send and falls back to a deterministic
  outgoing-message path when Mail's native reply body setter drops content.
- Keeps core runtime component updates atomic. Sirius stages replacement
  payloads first, then swaps the installed component into place instead of
  leaving partial runtime copies under Application Support.
- Replaces the Ollama Compatible Model Hub's fixed initial shortlist with
  remote Hugging Face GGUF search and paging. Searches such as `gemma` now query
  the full public GGUF catalogue, keep fit/ranking metadata, and expose Load
  more through Hugging Face cursors.
- Prevents model hub search cache bleed-through: a failed search page cannot
  silently reuse a cached page from another query or cursor.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

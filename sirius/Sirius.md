<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.77

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **`browser_use_find` is now a real find-in-page primitive.** It searches
  rendered document text (including non-interactive paragraphs and offscreen
  rendered text) in addition to the visible `browser_use` ref set, instead of
  only matching clickable/editable refs. Results carry a disambiguating `find`
  block (`text_match_count`, `ref_match_count`, `deduplicated_match_count`,
  `returned_count`, `omitted_count`, `match_limit`, `search_scope`,
  `empty_query`) and per-row `matches` tagged `kind: "text"` or `kind: "ref"`
  with excerpt, tag/role, `in_viewport`, `frame`, and `scroll_target`. A new
  `match_limit` argument (1–100, default 50) bounds match-heavy pages. An empty
  `matches` array now reliably means nothing matched in scope.
- **`api_request` resolves companion credential contracts.** When a requested
  requirement is a companion of an HTTP-capable contract, `api_request` now
  resolves to the parent HTTP contract automatically instead of failing
  `not_http_capable`, and reports a clear `ambiguous_http_contract` error when a
  companion maps to more than one HTTP contract. Permission-prompt metadata
  follows the resolved HTTP contract.
- **The distributable build defaults now target alpha.77/build 77.**

## Distribution

- Published as monotonic Sparkle build 77.
- Ships a refreshed signed core-runtime feed for the browser-use and credential
  broker changes.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

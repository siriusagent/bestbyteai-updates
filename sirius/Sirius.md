<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.45

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixed cross-provider session replay so Anthropic thinking signatures are not
  replayed into Gemini turns, and Gemini thought signatures stay scoped to
  Gemini-created assistant rows.
- Fixed cold-tier tool lookup for durable goals. `tool_search(select:goal)` now
  returns the model-facing `goal` schema when goal mode is enabled or an active
  goal exists.
- Replaced raw transcript error cards for `forced_tool_required` with compact
  inline summaries such as `bash - think required first`.
- Carries alpha.44 browser media-observation fixes forward.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

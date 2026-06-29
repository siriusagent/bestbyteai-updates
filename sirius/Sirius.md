<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.89

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Direct OpenAI-compatible providers ship as first-class citizens.** DeepSeek,
  Moonshot Kimi, Z.AI GLM, and xAI Grok are now recognized as direct
  OpenAI-compatible providers rather than generic OpenAI-compatible endpoints.
  The provider discovery, model roster, and API-key resolution paths handle
  each one explicitly, with matching environment variables and default
  settings, so the composer can resolve the right model and surface it without
  manual OpenAI-compatible wiring.
- **Composer provider selection is verified end-to-end.** The composer now
  resolves the configured direct provider for xAI and carries the resolved
  direct-provider entries through the payload used for model selection,
  with tests covering both the selection and the payload shape so a provider
  mapping regression is caught before it reaches a session.
- **`session_search` counts as real progress in tool cycles.** The tool-cycle
  progress signal now recognizes `session_search` results when they surface
  unseen hits, using a per-turn `SessionSearchHitTracker` that tracks hit-set
  novelty against flood thresholds. Genuine new hits break a cycle instead of
  being miscounted as repetition; empty or already-seen results still do not.
- **Background watches support keyed state-transition rules.** The watch rule
  system gains a keyed form (`anchor`, `key_group`, `state_group`,
  `target_state`) for polling monitors, so a row is judged on its own
  transition into the target state instead of being tripped by stale or
  re-printed rows that share a non-keyed condition. Non-keyed rules continue
  to work unchanged; `bash_status` and `bash` guidance describes when to reach
  for the keyed form.
- **The distributable build defaults now target alpha.89 / build 89.**

## Distribution

- Published as monotonic Sparkle build 89.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

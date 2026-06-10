<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.37

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixes Anthropic `claude-fable-5` turns failing with
  ``API 400: `temperature` is deprecated for this model.`` The Anthropic
  provider now treats Fable 5 and related no-legacy-sampling model families
  like the newer Opus 4 path: it omits `temperature`, `top_p`, and `top_k` from
  the wire request while still sending `max_tokens`.
- Keeps temperature/top-p/top-k support for Anthropic models that still accept
  those parameters, so existing Sonnet and Haiku settings are not flattened.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

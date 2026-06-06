<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.16

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Keeps `tool_cycle_blocked` recovery-control results out of the transcript
  body. Repeated empty `bash_status` polling still gets blocked by the engine,
  but the UI now surfaces that as compact status chrome instead of rendering a
  large red generic Tool card.
- Preserves normal `bash_status` transcript rendering for real status, output,
  and kill results.
- Prevents already-persisted orphan tool-cycle control results from replaying as
  stale red tool cards when a session is reopened.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

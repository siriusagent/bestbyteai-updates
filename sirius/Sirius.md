<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.18

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Wires SwiftPython ProcessPool structured telemetry into the Sirius host
  runtime before bootstrap warmup, so startup, command, stream, side-channel,
  callback, and worker lifecycle failures carry direct classification/reason
  fields instead of relying on screenshot-era inference.
- Adds session, worker, turn, command, stream, callback, and crash-evidence
  context to runtime diagnostics and recovery banners. This is the foundation
  for the in-app bug-report flow to generate grounded reports from user logs.
- Captures explicit `build_session` and `get_session_id` diagnostics from the
  session factory even when callers do not supply a telemetry context.
- Fixes recovery banner refresh handling so a newer respawn event is not
  cleared by a stale dismiss task from the previous banner instance.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

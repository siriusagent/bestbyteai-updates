<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.17

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Ships the hardened `bash_status` background-task lifecycle in the signed core
  runtime payload. Task-specific waits still work for known running `task_id`s,
  while blank/list-all waits return structured errors instead of feeding empty
  polling loops.
- Keeps completed background task records terminal and one-shot on the normal
  status surface so the model cannot keep re-polling stale terminal states as
  fake progress.
- Updates the Swift host runtime package to `swiftpython-commercial` `0.5.13`,
  picking up the public ProcessPool structured telemetry release.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

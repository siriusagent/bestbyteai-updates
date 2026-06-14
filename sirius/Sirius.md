<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.57

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **First-window engine boot cancellation no longer leaks workers.** Sirius now
  keeps engine boot owned by the app-lifetime runtime holder, so SwiftUI view
  task cancellation during early launch cannot abort startup after the worker
  pool has already spawned. Cancellation and non-timeout failures now clean up
  partial runtime state the same way timeout already did.
- **Pruned background tasks still show terminal event evidence.** If
  `bash_status` checks a task id after the completed task record was already
  pruned, queued events for that same task are returned in `recent_events` with
  guidance to inspect the evidence and stop polling the stale handle. Events
  for other tasks remain queued.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

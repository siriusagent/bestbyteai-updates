<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.78

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Background work attention controls.** Agent → Sub-agents settings now expose
  a Background Work section with auto-check, the unwatched-task check delay, the
  watched-task fallback delay, and the event-wake debounce. The values persist
  through Settings and tune how the agent wakes for and revisits background
  tasks.
- **Session handoff no longer loses memory on close.** Handoff closes now enqueue
  a deferred reflection job in a new `reflection_queue` table and a dedicated
  drainer processes it asynchronously, so session knowledge is reflected into
  memory without blocking shutdown. A config toggle controls LLM distillation
  during reflection.
- **Session factory internals reorganized.** Runtime/session component wiring was
  refactored for clearer module boundaries and to avoid circular dependencies.
  No host-visible behavior change.
- **The distributable build defaults now target alpha.78/build 78.**

## Distribution

- Published as monotonic Sparkle build 78.
- Ships a refreshed signed core-runtime feed for the reflection-queue and
  session-factory changes.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

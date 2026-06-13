<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.54

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Structured background watches.** Background `bash` tasks now support
  rule-based watches, completion policies, debounced wakeups, persistent scan
  offsets, and durable completion/failure events so monitors can wake the agent
  on meaningful output without shallow polling loops.
- **Parallel monitor isolation.** `execute_dag` bash steps keep independent PTY
  sessions, while Swift-hosted agent terminals now preserve background-owned
  commands across bridge generations and worker respawns instead of cancelling
  or reusing the wrong backend.
- **Safer background task control.** `bash_status(action="kill")` now verifies
  terminal-owned task termination before removing a task; unverified forced
  terminal kills stay registered as lost instead of silently disappearing.
- **Credential-capable detached backgrounds.** Explicit background tasks can
  use approved broker credentials through process-owned one-shot leases. Secrets
  are injected only into the detached child environment, redacted before durable
  task output is written, and never persisted in `background_tasks.json`.
- **CLI sub-agent live output.** CLI sub-agent stdout/stderr streams into
  progress tails for transcript annotations, and persisted sub-agent timeout
  settings are applied at dispatch time.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

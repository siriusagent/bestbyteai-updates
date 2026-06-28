<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.88

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Background-task kills are now host-verified.** `bash_status(action="kill",
  force=true)` on an auto-backgrounded Swift-terminal task no longer falls back
  to a 0.5s footer poll that leaves pidless tasks stuck as
  `terminal_signal_unverified`. The Swift terminal bridge returns a
  `TerminalKillVerification` computed from the PTY foreground process group
  before/after the signal and the in-flight capture state; when the host
  confirms the command is gone, the task is removed and reported
  `killed=true` (`verified_by="host"`). When death cannot be proven, the honest
  `terminal_signal_unverified` state is preserved. Older hosts fall back to the
  legacy poll path.
- **Terminal command captures always resolve.** `execCommandInTab` never leaves
  a pending capture dangling after a signal or tab closure:
  `terminal.command_finish` is logged on every exit, and a missing real
  completion footer yields a labeled synthesized result (`synthesized=true`,
  `synthesis_cause`) rather than an unmarked `-1`/`-130`. A real shell footer is
  always preferred.
- **Stale `terminal_signal_unverified` tasks are reconciled.** A terminal task
  left over from an unverified force-kill (`pid=null`, `pgid=null`, no live
  session, no footer) is no longer presented to future agents as live work:
  `bash_status(action="status")` reports
  `reason="terminal_unverified_stale"`, `actionable=false`, and
  `bash_status(action="kill")` removes it cleanly (`killed=true`) — no PID
  hunting or `background_tasks.json` surgery. A late footer reconciles to
  `completed`; a task that still has a session or process target stays honest
  `lost`.
- **Unified kill envelope.** Detached process-group kills, host-verified
  terminal kills, and footer-verified kills share one result envelope with a
  `verified_by` provenance field. The detached kill path is otherwise unchanged.
- **The distributable build defaults now target alpha.88 / build 88.**

## Distribution

- Published as monotonic Sparkle build 88.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

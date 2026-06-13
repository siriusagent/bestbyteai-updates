<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.56

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Background watches recover across idle worker respawn.** Sirius now replays
  the same background-event sink into rebuilt worker sessions, and idle sessions
  with armed watches or pending background tasks rearm the sink without waiting
  for the next user or model turn.
- **Background watch callbacks use the async bridge path.** Fired watch events
  can arrive while no synchronous command response channel is active, so the
  host callback is now registered and invoked through SwiftPython's async
  callback API.
- **Queued watch events are replayed when a sink is installed.** Alerts that
  fired during a respawn or session-start gap can still wake the host, while the
  durable queue remains authoritative for the next status drain.
- **Session resume and restart paths wire background watch callbacks.** Sidebar
  resume and fresh-session restart now register and pass the background event
  sink alongside sub-agent and permission callbacks, with failure cleanup for
  the newly registered sink.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

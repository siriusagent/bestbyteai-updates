<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.036

Alpha.036 brings a dedicated Goal panel, clearer control over long-running work,
and a substantial upgrade to native browser interaction.

## A home for your goals

- Open the Goal panel to inspect the objective, progress, verification evidence,
  usage, safeguards, and history in one place.
- Pause and resume work, adjust output and active-time limits, and review the
  scope without losing the goal's durable record.
- Interrupted work offers an explicit recovery path. Missing usage reports and
  exhausted safeguards stop continuation with a recorded reason.
- Completion requires evidence and respects unfinished linked-plan work.
  Progress checkpoints and control actions remain attached to the correct goal
  across turn boundaries and worker recovery.

## More capable browser interaction

- Native mouse and keyboard input now belongs to the browser view, with improved
  focus, scrolling, selection, and restoration behavior.
- Actions revalidate their targets and retain evidence of what happened,
  helping the agent distinguish a successful interaction from an uncertain one.
- Native dialogs expose their decisions to the agent. WebKit callbacks and
  download lifecycles have explicit ownership and cleanup.
- AutoFill reveals the revalidated native target, and browser strategy reviews
  use retained action evidence to guide the next attempt.

## Runtime hardening

- Updated the complete matched SwiftPython runtime to 0.6.0-duplex.8.4, including
  fixes for object ownership, conversions, callbacks, worker lifecycle, and
  queue performance.
- Browser outcomes and worker-pool lifecycle events are handled independently,
  so a browser interaction does not masquerade as a runtime failure.

Requires macOS 26 or later on Apple silicon.

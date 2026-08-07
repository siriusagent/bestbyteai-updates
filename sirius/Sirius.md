<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.014

This alpha completes Sirius's full-duplex active-turn control path — queued
guidance, interrupt-and-steer, Stop, and Goal controls with exact
request/turn correlation — and replaces opaque tool suppression with a
recoverable, honestly-reported error backoff policy.

Updating from `0.1.1-alpha.012` also picks up everything prepared for
`0.1.1-alpha.013`, which never reached the update feed.

## Highlights

- **Granular active-turn guidance.** Steer waits for the next safe point, while
  Interrupt & Steer deliberately truncates generation first. A single global
  coordinator keeps every receipt, interruption, and application paired with
  the exact queued request.
- **No duplicate or blind control delivery.** Sirius uses the published
  `swiftpython-commercial` `0.6.0-duplex.5` receipt contract and never
  resubmits a possibly owned control. Owned, rejected, pending, and
  delivery-uncertain outcomes remain distinct.
- **Typed Goal control.** Pause and Clear travel through the active duplex turn
  when one exists; idle Goal mutations run as short duplex turns and terminate
  with explicit product success instead of a false UI failure.
- **Stronger terminal and recovery truth.** `Done` is the sole normal product
  fence. Error, lifecycle, transport, interruption, and durable ledger evidence
  are reconciled separately, and worker replacement finalizes the exact failed
  turn without replaying an explicit Stop or mutation-boundary failure.
- **Tool errors no longer silently strand a turn.** After two consecutive
  errors a tool is suppressed from the model surface — but the suppression is
  now reported as exactly that, with the error count, threshold, and current
  recoverability, instead of looking like a missing or deregistered tool.
- **Bounded, explicit tool recovery.** The model receives the exact recovery
  action for every newly-suppressed tool and may restore it once per unresolved
  failure episode. A successful call proves progress and starts a fresh episode;
  exhausted names are told to choose another tool or report the blocker.
  Accepting new user guidance renews eligibility without erasing failure
  evidence.
- **Consistent policy across every dispatch path.** Builtin, MCP,
  host-delegated, pinned, and loop-owned tools follow one rule, and
  `execute_dag` children are gated and accounted for identically — a dependent
  step can no longer bypass backoff or act on a stale pre-failure snapshot.
  Pinning a tool ("Always include") is a ranking guarantee, never a safety
  bypass.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 139 with the matching signed core-runtime feed.

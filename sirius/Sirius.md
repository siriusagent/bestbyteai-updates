<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.013

This alpha completes Sirius's full-duplex active-turn control path: queued
guidance, interrupt-and-steer, Stop, and Goal controls now share exact
request/turn correlation, explicit application truth, and durable recovery.

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
- **Durable, bounded application state.** Exact control identities commit with
  transcript mutation, attachment-bearing steer fails explicitly, progress is
  bounded, and ordered application events remain the sole authority for queued
  user bubbles.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 138 with the matching signed core-runtime feed.

<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.015

This is a focused reliability hotfix for long-running model turns. A healthy
worker may now remain silent for more than 60 seconds while a model or
accelerator is still working without Sirius falsely terminating the turn.

## Fixed

- **Removed the false 60-second duplex failure.** The matched SwiftPython
  control reader now treats an empty receive interval as a liveness poll rather
  than `runtimeUnavailable`.
- **Preserved real failure truth.** Worker death, channel closure, protocol
  failure, and explicit session deadlines still terminate with their typed
  failure; the fix does not add synthetic progress or weaken timeout policy.
- **Kept active-turn controls intact.** Steer, Interrupt & Steer, Stop, and Goal
  controls continue to use the exact durable receipt and no-replay contract
  introduced in the previous alpha.

## Runtime

- Exact `swiftpython-commercial` `0.6.0-duplex.6` Runtime, private Engine, and
  matched worker.
- Worker wire v6 and duplex media v1 are unchanged.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 140 with the matching signed core-runtime feed.

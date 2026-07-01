<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.99

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This is a **hotfix release** over alpha.98. It fixes degraded computer-use
action summaries and refines state-attribute verification for UI elements.

## Changes

- **Action summaries name the acted element and its context.** Desktop action
  envelopes now carry a structured `ActionTarget` that captures the acted
  element's identity plus the owning application/window. Summary generation no
  longer degrades to generic placeholders such as "Interacted with ." — the
  transcript reports what was acted on and where.
- **Verifier distinguishes "no state" from "unconfirmed."** `ComputerActionVerifier`
  now returns a distinct `notApplicable` result for elements that carry no state
  attributes, instead of conflating them with `unconfirmed` outcomes. Action
  reporting and tests reflect the new tri-state.
- **Regression coverage expanded.** Swift and Python tests pin the new
  summary-target behavior, the `notApplicable` verifier path, and snapshot
  projection of acted-element context.
- **The distributable build defaults now target alpha.99 / build 99.**

## Distribution

- Published as monotonic Sparkle build 99.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

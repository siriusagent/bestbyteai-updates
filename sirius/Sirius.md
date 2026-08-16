<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.025

Alpha.025 is a focused hotfix for Telegram and other generic messaging
channels when Auto permissions are enabled.

## Channel hotfix

- **Incoming channel messages reach Sirius again.** Per-user channel sessions
  now receive an isolated permission context with a fresh synchronization
  lock. This removes the pre-model failure that silently swallowed messages
  after the Auto-permissions update.
- **Unexpected early failures are visible.** If channel setup fails before the
  model turn begins, Sirius logs the failure and returns a retry message to the
  sender instead of dropping the task without feedback.
- **Transport and model behavior are otherwise unchanged.** Telegram polling,
  channel routing, provider selection, permissions, and reply delivery retain
  their existing contracts.

## Verification

- The non-slow engine gate passed 7,814 tests with 17 skips and 13
  deselections; the full Swift host gate passed 3,365 tests with 20 skips.
- The focused channel and permission regression gate passed 671 tests with 7
  skips.
- Ruff, generated-wiki drift, and diff checks passed.
- The signed release bundle carries the matching updated core-runtime feed.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 150 with the matching signed core-runtime feed.

<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.012

This alpha hardens the native runtime boundary, restores the right workspace
when moving between live chats, and finishes Sirius's field-attached native
WebKit AutoFill path.

## Highlights

- **Hardened SwiftPython runtime.** Sirius now ships against
  `swiftpython-commercial` `0.6.0-duplex.4` and its published Runtime surface.
  Worker policy, sandbox execution, cancellation escalation, structured
  telemetry, and stale-handle recovery retain the existing Sirius behavior
  while reducing exposure to private runtime implementation details.
- **Native WebKit AutoFill stays attached to the focused field.** The key
  affordance preserves focus and opens WebKit's real macOS menu at the correct
  field, so Passwords, Contacts, and payment options remain owned by WebKit and
  macOS. Every eligible field now uses one stable `key.fill` symbol instead of
  changing chrome by field classification (BUG-396, BUG-397).
- **Live chats restore their own workspace.** Re-selecting an activated chat
  restores its workspace strip and DiffTree root from the session's start
  configuration without restarting or mutating the worker (BUG-395).
- **SiriusMarkdown 0.6.25.** Decorated links keep an immediate native fallback,
  visible favicons replace it in place, narrow table cells refresh correctly,
  and decoration plus the first label token wrap as one unit.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 137 with the matching signed core-runtime feed.

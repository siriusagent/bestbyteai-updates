<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.034

Alpha.034 is a launch hotfix for Alpha.033. Nothing else changes.

## Sirius opens again on macOS 26.5

- Alpha.033 could not be opened on macOS 26.5 ("The application 'Sirius' can't
  be opened"). Its signature was valid and notarized, but its Keychain access
  group entitlement was not backed by the provisioning profile macOS 26.5
  requires, so the system refused to start it. Macs on earlier 26.x builds were
  not affected.
- Alpha.034 embeds a Developer ID provisioning profile for `com.sirius.agent`,
  which macOS 26.5 accepts. It was launch-tested on macOS 26.2 and 26.5.2
  before publishing.

## Your secrets are unaffected

- Every stored API key, token, and channel secret keeps working, including any
  you already moved with **Upgrade protection…** in Alpha.033.
- Settings → Credentials & Access → Storage & Access continues to report the
  Data Protection Keychain as **Available** and offers per-item upgrades.

## Everything from Alpha.033 remains

The stable toolbar AutoFill control, the Credentials & Access pane, loss-safe
Keychain replacement, and component update discovery ship unchanged.

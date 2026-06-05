<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.7

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixes the iMac launch failure where a downloaded, quarantined Sirius install
  could show "Sirius is damaged and can't be opened" even though `spctl` and
  `codesign` accepted the copied app.
- Normalizes the embedded Python framework so only Mach-O files retain
  executable bits. Plain Python helper scripts are no longer treated as
  executable payloads by LaunchServices, syspolicyd, or XProtect.
- Adds a release-gate check that rejects executable-bit non-Mach-O Python files
  before a DMG can ship.
- Keeps the public app build on the no-seed runtime path: the signed app does
  not bundle `sirius_agent`; it installs the core runtime from the signed Sirius
  runtime feed after first-run setup.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key and update feed are enabled for alpha update testing.

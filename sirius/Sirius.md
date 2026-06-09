<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.34

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixes bash credential injection for wrapper scripts that read broker-managed
  environment variables internally. Approved bash credentials can now be carried
  into a command-bound execution lease through explicit `credential_requirements`
  metadata or the short-lived pending intent created by `credential_request`.
- Keeps credential grants non-ambient: secrets still do not enter the visible
  command text, do not persist in the terminal environment, cannot be used by
  detached background jobs, and are resolved only when a one-shot lease is
  minted for the command.
- Adds regression coverage for Kalshi-style multi-credential wrapper commands,
  one-shot pending bash intents, unknown/incompatible requirement failures,
  environment-dump blocking, and no-ambient-env behavior after a credentialed
  command completes.
- Updates the credential broker runbook, generated wiki, and bundled skill
  guidance so future bash commands that need wrapper-script credentials pass
  `credential_requirements` instead of relying on env-var text appearing in the
  shell command.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

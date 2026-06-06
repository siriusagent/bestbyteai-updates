<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.15

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Stops session switch and new-chat handoff closes from submitting
  post-session reflection to the stale outgoing worker after the UI has already
  switched away.
- Handoff closes now run only the cheap worker cleanup path (`close_session` and
  handle/callback release), while explicit/window close and Cmd-Q still run
  post-session reflection.
- Keeps lifecycle diagnostics explicit when handoff reflection is skipped,
  including the close reason, switch target, draining state, and
  `no Python traceback captured`.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

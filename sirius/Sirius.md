<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.53

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Background task wakeups no longer create fake user bubbles.** Idle
  background-task polls and watch events now run as hidden runtime-control turns:
  the model still sees the control instruction, but the transcript does not
  persist or render it as a human-authored message.
- **OAuth sign-in retries release the loopback port immediately.** Provider
  sign-in sheets now retain and cancel the active `OAuthLoopbackListener` on
  Retry, Dismiss, Cancel, Save, auth-method switches, and sheet close. Cancelled
  callback waits also tear down the listener instead of leaving the fixed
  callback port bound until timeout.
- **Sub-agent work stays readable without transcript row growth.** Sub-agent
  dispatch and lifecycle beats stay standalone in the transcript and expose
  agent, task, status, elapsed time, lifecycle detail, output/error text, and a
  compact Work timeline through the annotation popover.
- **CLI sub-agent output is decoded as UTF-8 consistently.** Raw CLI adapters
  now decode subprocess text with UTF-8 plus replacement semantics, avoiding
  ASCII-locale crashes when child agents emit symbols or non-ASCII text.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

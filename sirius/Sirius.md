<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.85

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Tool-cycle recovery is now a recovery-only micro-context.** When the engine
  detects a stuck tool loop, instead of forcing another full iteration over the
  same context, it makes one isolated diagnostic call that sees only the cycle
  facts and must return a typed recovery decision: answer the user, ask a
  clarifying question, switch tools, or search for a new tool. The cycled tool
  stays blocked through the recovery, and invalid or exhausted recovery ends the
  turn with a clear message instead of looping.
- **Clarifications no longer create a blank plan.** Asking a clarifying question
  before a plan exists — including the new recovery "ask the user" path — no
  longer mints an empty placeholder plan or a blank `plan.md` artifact. A plan is
  written only once the model actually proposes one. The clarification card and
  its answer flow are unchanged; plan-bound clarifications behave exactly as
  before.
- **The distributable build defaults now target alpha.85 / build 85.**

## Distribution

- Published as monotonic Sparkle build 85.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

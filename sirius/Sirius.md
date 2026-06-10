<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.38

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixes goal mode silently stopping while the goal pill still showed
  **Active**. A single narration-only reply (a turn with zero tool calls)
  used to disable autonomous continuation permanently; the engine now
  tolerates quiet turns up to the configured "No-progress Suppression"
  threshold before halting, and records a visible goal checkpoint when
  continuation is actually suppressed.
- Autonomous goal turns can no longer end as pure narration: the engine
  challenges a text-only stop and requires real tool work, an
  evidence-backed `goal(action='progress')` checkpoint, or a
  `goal(action='complete')` claim before the turn may end. Persistent
  refusals force-end the turn observably instead of spinning.
- Errored, interrupted, or timed-out turns never signal goal continuation
  anymore, so a wedged turn cannot auto-retry itself under an active goal.
- Strengthens the model-facing goal-mode contract so the agent is told
  explicitly that narration-only turns suspend durable autonomy.
- Fixes attaching a non-PDF document (docx, txt, md, …) on Anthropic models
  failing the whole turn with
  `API 400: …document.source.base64.media_type: Input should be
  'application/pdf'`. Non-PDF attachments now reach the model as extracted
  text (plain-text files use Anthropic's native text-document form), and
  Gemini gains the equivalent safeguard for unsupported inline document
  types.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

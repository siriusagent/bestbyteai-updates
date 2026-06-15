<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.63

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Background task wakes are durable and retryable.** Sirius now claims
  background-event evidence before running an idle wake or goal continuation,
  acknowledges it only after the stream finishes, and releases it for retry if
  the wake is cancelled or fails.
- **Status checks coordinate with host wakes.** `bash_status` now returns
  structured `recent_event_records` while preserving events already claimed by
  the Swift host, so model-side polling cannot steal wake evidence.
- **Wake lifecycle is visible in the macOS app.** Transcript annotations and the
  Goal status popover now show event phase, severity, sequence, ownership, and
  timing details for queued, running, retry-pending, and acknowledged wakes.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

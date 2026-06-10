<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.39

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Goal mode now tolerates short stretches of narration-only turns before ending
  durable continuation.
  `done` is only emitted with explicit model-facing continuity conditions,
  and continuation suppression is surfaced via a `continuation_suppressed`
  checkpoint.
- Anthropic attachment projection is now backend-safe: non-PDF file docs use
  doc text extraction (or Anthropic text-document block for `text/plain`) instead of
  sending unsupported inline document MIME payloads.
- Gemini now shares the same inline document gating, and goal-mode provider settings
  are hot-applied to active workers.
- MCP support was expanded with tool classification, preflight visibility,
  richer provider transport handling, and safer restart/live-reload behavior so
  tools stay aligned after settings changes.
- Added the native `Report Bug` flow in the app, including local evidence bundles
  (logs, session context, diagnostics) and optional model-assisted issue drafting.
- Interruptible tool execution improved: pause/steer can stop long-running turns
  at the in-flight boundary, and `bash` interrupts now preserve partial output
  while completing with a real completion footer.
- Wallet rail work advanced with method-aware request fingerprints and protocol-aware
  checkout execution constraints.
- Dynamic UI chart/table/timeline tool output now ships hardened rendering paths and
  richer normalization for model-shaped data.
- Sparkle auto-update pipeline is now fully in the signed release path, including
  signed appcast generation and core-runtime metadata injection.
- Core runtime updates are guarded by signed runtime feed manifest checks and are
  rebuilt from the exact seeded inputs for this app version.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

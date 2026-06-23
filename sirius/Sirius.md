<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.79

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Assistant feedback now actually steers the persona.** Per-message 👍 / 👎
  ratings feed the personalisation profile through two deliberately asymmetric
  paths:
  - **👍** is immediate and richer — it appends a one-sentence lesson (up to
    140 characters, a "tweet budget") to *Do more of* on each click.
  - **👎** no longer burns a per-click model call that was logged and thrown
    away. It now queues the evidence and, once enough downvotes accumulate
    (default 5) or a 48-hour fallback fires, a background pass distils 0–2
    behavioral *Avoid* entries (140–280 characters, style/tone only — never
    topic-specific), behind validation gates with a recoverable audit trail.
- **New Behavior Defaults controls.** Agent & Sub-agents → Behavior Defaults
  gains an *Assistant feedback* section: toggle thumbs-down distillation,
  set the downvote threshold (2–20), and choose the stale-queue fallback
  (24 h / 48 h / 72 h / Never).
- **Locks and curation honored.** `do_more_of` / `avoid` remain hand-editable
  in the Mind → Profile surface; `*_locked` flags freeze a list against
  automatic writes.
- **The distributable build defaults now target alpha.79 / build 79.**

## Distribution

- Published as monotonic Sparkle build 79.
- Ships a refreshed signed core-runtime feed for the assistant-feedback
  distillation engine, queue table, and config changes.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

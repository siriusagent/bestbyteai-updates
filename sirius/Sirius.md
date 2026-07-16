<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.122

**Strict pre-release unstable build.** This alpha is for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This release makes long-running Goals easier to trust at a glance, adds local
Tool Activity diagnostics, keeps DiffTree Markdown readable while you resize,
and hardens macOS Automation so Mail and other apps are less likely to freeze
or leave half-finished work behind.

## Goal status and usage

- **Goal usage now reflects new work, not prompt replay.** Sirius counts
  uncached input plus output for the active Goal, so long runs no longer look
  inflated just because the same context was reread from cache.
- **The Goal control shows what matters while work is in flight.** State,
  elapsed time, Goal usage toward your checkpoint, and current context fill are
  visible together, with one clear lifecycle action for the current state.
- **Usage updates while tools are running.** The meter advances during a Goal
  turn instead of waiting for the turn to finish.

## Tool Activity diagnostics

- **See which tools Sirius has ready.** The Activity sub-tab under MCP, Tools &
  Skills shows which tools were ready, available on request, hidden, or no
  longer available in each session—and explains why in plain language.
- **Find reliability problems without inspecting logs.** A sortable local table
  shows lifetime or exact-workspace calls, tool errors and rate, average time,
  recorded results, last use, and on-demand activation totals. Removed and
  currently unavailable tools remain visible when they have history.
- **Diagnostics stay metadata-only and local.** Sirius stores and displays tool
  names, scopes, counters, timestamps, duration, tiers, and reasons—not tool
  arguments, outputs, prompts, commands, URLs, raw errors, screenshots,
  credentials, or transcript content.

## DiffTree Markdown preview

- **Markdown previews keep their spacing when the panel resizes.** Preview
  layout waits for the real content width, then relayouts cleanly instead of
  stacking overlapping lines after a window or display change.

## macOS Automation reliability

- **Mail body search no longer freezes Mail.** Sirius no longer asks Mail to
  scan message bodies in ways that can hang on uncached IMAP content.
- **Automation fails closed on slow or partial work.** Contacts, Messages,
  Notes, Reminders, Calendar, and related helpers bound heavy queries, discard
  failed compose attempts, and report unavoidable partial sends instead of
  pretending a write finished.
- **Custom scripts stay reviewable.** Raw automation scripts show a redacted
  approval preview, validate size and arguments, and bind remote passkey
  approval to the exact script being authorized.

## Notes

- **Sparkle build version** is `122` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `121` or earlier will offer
  this release.
- The signed core-runtime feed is refreshed as `0.1.0-alpha.122` so the app,
  appcast, and Python runtime component remain release-synchronized.

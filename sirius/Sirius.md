<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.119

**Strict pre-release unstable build.** This alpha is for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This is a focused transcript reliability release. Inline tool details respond
consistently in live and historical tasks, and large task switches no longer
show a transient pile-up of rows while the destination transcript settles.

## Reliable inline tool details

- **Inline tool cards expand and collapse when pressed.** Grouped activity,
  search results, and inline action detail now mutate the visible conversation
  state and refresh the existing row host, so the disclosure remains responsive
  without replacing transcript views.
- **Expanded content reflows the rows below it correctly.** Sirius uses native,
  non-nested macOS buttons and propagates the changed row height through the
  persistent AppKit transcript layout in both live and restored history.

## Clean task switching

- **Large task switches wait for destination row heights before revealing the
  transcript.** Provisional row hosts are clipped to their bounds, preventing
  messages, tool cards, and action bars from briefly drawing on top of one
  another.
- **Progressive history loading uses generation-safe settlement.** Prepending
  older rows now waits for the current task, layout stage, width, and row
  identities instead of relying on a fixed frame delay, preserving the scroll
  anchor across heavy transcripts.

## Notes

- **Sparkle build version** is `119` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `118` or earlier will offer
  this release.
- The signed core-runtime feed is refreshed as `0.1.0-alpha.119` so the app,
  appcast, and Python runtime component remain release-synchronized.

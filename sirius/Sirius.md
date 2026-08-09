<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.016

This alpha improves Browser reliability and evidence fidelity, and closes
several control-path failures found while exercising real browser workflows.

## Changed

- **Native content blocking is on by default.** Sirius ships a pinned,
  provenance-recorded EasyList conversion and installs it before the first
  WebKit navigation. Compilation is content-addressed, failures remain
  fail-open, and Browser settings include a single global off switch.
- **Browser evidence is more complete and truthful.** Page-text length and
  truncation are explicit, safe older browser controls remain available to the
  model wire format, and compact control paging reports listed, delivered, and
  omitted counts rather than silently hiding the tail of a page.
- **Browser history selection is explicit.** Typing in the address bar no
  longer silently selects the first suggestion; Return uses the typed value
  until a history row is deliberately selected.

## Fixed

- **Goal Pause is a real durable action.** A model-owned pause records its
  reason and exact resume checkpoint, stops continuation, and cannot be
  confused with a read-only Goal view.
- **Idle recovery uses the complete typed duplex contract.** `/recover`, Goal
  controls, and their production adapter now agree on method names and turn-ID
  positions, including the narrow session-publication race.
- **Transient peer disconnects during reasoning retry safely.** A disconnect
  can retry after reasoning-only stream fragments, while any assistant text or
  tool-call fragment still prevents replay.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 141 with the matching signed core-runtime feed.

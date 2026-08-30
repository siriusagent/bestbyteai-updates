<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.2-alpha.003

Alpha.003 makes long-running work stay cheap to reopen and continue. It also
restores autonomous Goal creation for genuine multi-turn requests and replaces
the blunt per-turn token-only stall cutoff that could halt corrective work.

## Long conversations load what you can see

- Opening a persisted conversation now fetches a bounded newest page instead of
  every message, replay event, and attachment. The normal target is 160 timeline
  items; a user-turn boundary may extend the page to a hard maximum of 256.
- Older history loads one page at a time only when you reach the real top edge.
  Duplicate scroll notifications coalesce, and AppKit preserves the visible row
  and pixel offset while rows prepend—there is no forced jump back to the tail.
- A single exceptionally large turn continues across bounded pages instead of
  making the whole conversation fail to open.

## Continuing work no longer rehydrates everything

- A resumed worker receives the opening objective, a bounded recent tail, and a
  private recall marker when older durable history was omitted. Exact older
  evidence remains available from SQLite through session search.
- The in-worker transcript keeps a bounded recent resident window while tracking
  the full logical count and absolute durable ordering, so the next message
  cannot overwrite or collide with omitted history.
- Forking an attachment-heavy conversation remaps copied attachment references
  with one set-based transcript update instead of rescanning every message once
  per attachment.

## Goals get room to recover

- Sirius can again start a durable Goal when the current request clearly needs
  work across turn boundaries; provenance and explicit Goal-denial rules still
  apply.
- The no-progress backstop now requires both 250,000 prompt tokens and three
  model calls since authoritative progress. A failed action can replan and make
  a corrective attempt without an immediate sledgehammer stop.

## Notes

- Sparkle build version is `159` (`CFBundleVersion`), the primary auto-update
  comparison key. Apps on build `158` or earlier will be offered this release.
- The signed ABI-1 core-runtime feed advances to engine version
  `2026.08.30.4`, built with app version `0.1.2-alpha.003`.

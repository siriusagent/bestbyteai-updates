<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.002

**Alpha channel release.** Sirius's core product surfaces and signed update
path are stable enough for regular use. The alpha label remains a pre-1.0
release channel — updates may still refine behavior and compatibility — but
this is a user release, not an installation or packaging test.

This release expands native macOS Automation into richer Music, Contacts,
Notes, Reminders, and Calendar workflows; makes session approvals grant the
useful capability instead of one exact action; keeps permission waits alive
under host resource pressure; restores Show more/Show less for long skill
prompts; and pins SiriusMarkdown `0.6.20` so live table streaming stays
bounded and attachment serialization is safe.

## Richer native macOS Automation

- **Apple Music joins the native Automation suite.** Ask mode can inspect
  playback and library metadata; Agent mode can control playback, volume, and
  shuffle behind the same action-scoped approval gate as the other Apple app
  tools.
- **Contacts, Notes, Reminders, and Calendar cover more real workflows.**
  Create and update contacts; create Notes folders and append; target
  Reminders lists and update fields; update Calendar events with location,
  description, and URL. The scripting dictionary can search ranked terminology
  directly, and `macos_script` can compile-check AppleScript/JXA without
  execution and shape successful output as JSON or JSON Lines.
- **Mail account targeting and compose rollback are side-effect safe.** Named
  account lookups materialize lazy JXA specifiers before accepting them;
  compose validates the sender/account pair before creating an outgoing
  message; failed post-create checks close without saving instead of leaking a
  Draft. Compose can bind From to an exact enabled account and distinguish
  Mail acceptance from verified delivery.
- **Patch-style updates no longer treat provider-filled defaults as
  destructive intent.** Empty/false/zero/list defaults are discarded before
  JXA is generated. Deliberate clears and false/zero writes use an app-scoped
  `update_fields` contract that validates before dispatch and surfaces the
  selected fields in approval metadata.

## Approvals that match how you actually work

- **One session approval covers the useful capability, not one exact
  action.** **Allow Music/Contacts/Notes/Reminders/Calendar for This Session**
  covers every mutation on that canonical tool. Outbound Mail and Messages
  stay separately gated as communication; Mail's local mutations have their
  own tool grant; raw scripts stay one-shot; PLAN mode still denies every
  mutation. Typed grants are bound to the approval prompt, held only in
  memory, and retained across live permission-preset changes.
- **A permission prompt can no longer lose its live turn to resource-pressure
  shedding.** SwiftPython Commercial 0.5.18 keeps callback-returned async
  Futures busy through settlement and explicit worker acknowledgement. Sirius
  therefore retains pressure throttling, rejection, and safe idle shedding
  while the wait and its in-memory session grants survive.
- **Compile-only instructions no longer hide `macos_script`.** Tool-
  prohibition parsing now requires an explicit "do not call/use" phrase, so
  prose such as "compile (do not execute) this JXA with macos_script" does
  not accidentally make the tool unavailable later in the same turn.

## Transcript and Markdown polish

- **Long skill-token prompts once again get Show more/Show less.** The native
  skill-chip route previously bypassed both disclosure paths, so a single
  `imagegen` release prompt could dominate the transcript. Skill flow now
  measures its full native wrapped height, applies a six-row faded preview on
  real overflow, and exposes a bounded marker-free accessibility summary while
  collapsed.
- **SiriusMarkdown `0.6.20` keeps live GFM tables bounded end-to-end.**
  Unchanged table-cell render models are reused across mutable-tail reparses;
  stable groups of completed rows use explicit render tokens and cached
  natural sizes so a growing suffix does not trigger triangular body work;
  default cells carry exact width-specific line layouts, CoreText paint plans,
  and row heights into SwiftUI. Transparent attachment placeholders and tinted
  math attachments use bitmap-backed images TextKit can serialize safely.
  Assistant, user-bubble, plan, and DiffTree Markdown pick this up with no
  app-side table workaround.

## Notes

- The bundled channel client now consumes SiriusMsg `0.0.1-alpha.13`, including
  transport-only reconnects, typed attachment integrity failures, and current
  service restart/send-deadline hardening.
- **Sparkle build version** is `127` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `126` or earlier will offer
  this release.
- The signed core-runtime feed is refreshed as `0.1.1-alpha.002` so the app,
  appcast, and Python runtime component remain release-synchronized.

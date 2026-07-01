<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.101

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This release tightens up two things that got in the way during a web-research
session: messy article extraction and toolbar toggles that weren't actually
doing anything.

## What's new

- **Cleaner web reading on structured pages.** Articles from encyclopedias,
  docs, and other citation-heavy sites now extract as real readable text
  instead of a jumble of broken sidebar tables, `[citation needed]` markers,
  and stray `[[4]]` reference brackets. Pages that are mostly data tables
  (e.g. "list of countries by GDP") now come through with all their rows
  instead of a truncated stub.
- **The "Temporary chat" toggle now means it.** Turning it on in the QuickMenu
  starts a chat that lives only in memory — it no longer quietly writes the
  conversation to your local database.
- **The "Memory & profile nudges" toggle now reaches the engine.** Switching
  it off for a session actually mutes memory and profile nudges for that
  session, instead of flipping in the UI with no effect. A global Settings
  change still applies to new chats; the toggle only adds a per-session mute.
- **Various stability and test improvements.**

## Distribution

- Published as monotonic Sparkle build 101.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

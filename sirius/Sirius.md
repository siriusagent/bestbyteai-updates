<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.28

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixes `apple_mail.search` so sender-, subject-, and message-id-scoped
  searches use Mail-native filters instead of timing out after scanning all
  messages.
- Stops Mail timeout summaries from reading as successful zero-result searches
  in the transcript.
- Hardens the rest of macOS Automation: Contacts, Notes, Reminders, Messages,
  and Calendar now fail fast on missing required handles or broad unscoped
  searches, and Calendar event searches require `calendar` unless
  `all_calendars=true` is explicit.
- Updates Notes, Reminders, and Calendar search paths to use native app filters
  before falling back to slower enumeration.
- Keeps the raw script escape hatch from rejecting unrelated prefix app names
  such as MailMate while still blocking canonical Mail automation.
- Removes hardcoded repository defaults on new installs: owner now starts
  blank, branch prefix now starts blank, and leaving owner empty creates new
  GitHub repositories under the connected account at action time instead of
  persisting a personal or organization fallback.
- Clarifies GitHub setup as optional saved GitHub access. Users can connect a
  personal GitHub account or a dedicated agent account; Sirius no longer frames
  this as a required separate Sirius-owned GitHub identity.
- Fixes stale per-worker MCP tool discovery. New sessions now pass the current
  persistent config snapshot into the selected Python worker before session
  construction, so enabled MCP servers such as Robinhood appear no matter which
  worker receives the chat.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

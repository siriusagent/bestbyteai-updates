<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.116

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This release adds a new context usage breakdown to the composer, fixes tool
calling for API-key GPT-5.6 models, repairs two Dark Mode regressions, makes
PDF text extraction more trustworthy, and closes out a broad reliability and
security sweep across every messaging channel (Telegram, Discord, WhatsApp,
Google Chat, IRC, SMS, and iMessage).

## What's new

- **See exactly where your context window is going.** Clicking the context
  ring in the composer now opens a breakdown of your current conversation's
  token usage by category — System prompt, Tool definitions, Skills, MCP &
  dynamic tools, Subagent definitions, Summarized conversation, and
  Conversation — with a stacked usage bar and a clear label for whether the
  numbers are an estimate or confirmed by the model provider.

## Fixed

- **GPT-5.6 models used with your own OpenAI API key now support tool calls
  correctly.** Previously, using tools together with reasoning on these
  models could fail or silently drop your configured reasoning level. Sirius
  now routes these requests through the API path that supports both at once,
  while other OpenAI-compatible providers are unaffected.
- **The token/usage counter in the status bar no longer inflates.** Switching
  models mid-conversation, or reopening a session, could make the displayed
  token count balloon past the real total. It now stays accurate.
- **Dark Mode no longer renders chat text in black.** Assistant replies —
  paragraphs, headings, lists, and tables — now use readable, correctly
  colored text when Dark Mode (or a forced dark theme) is active.
- **Switching between Auto, Light, and Dark theme no longer loses your open
  chat.** Changing the appearance setting could unexpectedly swap your
  current conversation for a new, empty one. Theme changes now preserve
  whatever you were doing.
- **More reliable text extraction from PDFs.** A rare PDF text-extraction bug
  could silently drop certain letters from a document (for example, turning
  "expand" into "expan"), producing readable-looking but corrupted text.
  Sirius now cross-checks extracted PDF text and automatically falls back to
  a second extraction method if the primary result looks damaged, so a bad
  result can't quietly slip through — including for documents that were
  already cached from a previous version.

## Messaging channels — reliability and security

This release includes a large hardening pass across every connected
channel (Telegram, Discord, WhatsApp, Google Chat, IRC, SMS, and
iMessage):

- **Provider and account changes now apply instantly.** Switching your AI
  provider, model, or account in Settings now takes effect immediately for
  connected channels — no app restart required, and no risk of a channel
  silently continuing to use the old provider.
- **No more duplicate replies.** Channels could occasionally send the same
  reply twice after a slow response — for example on a long tool call or a
  large attachment. Replies are now delivered exactly once, even if a
  response takes unusually long.
- **Channels recover from dropped connections automatically.** If a
  channel's connection died unexpectedly (for example Telegram or Discord's
  live connection dropping), it could stop receiving new messages until the
  app was restarted. Dead connections are now detected and automatically
  reconnected.
- **Messages from different conversations are no longer confused with each
  other.** In rare cases, a message in one conversation could be mistakenly
  treated as a duplicate of an unrelated message in a different conversation
  and get silently dropped.
- **Permission and tool-approval changes now reach every channel
  immediately.** Updates to your allowed tools, bash commands, or approval
  rules in Settings now reliably apply to background channel conversations,
  not just the currently open chat window, and Sirius double-checks after
  saving that the change actually took hold.
- **Passkey approvals in Safari are more reliable.** Approving a channel
  action via a Safari passkey prompt could, in rare cases, time out even
  after you approved it in time. That window has been closed, and the
  generic channel-approval flow now uses a safer, more consistent
  return-to-app handoff.
- **Long-running channel requests no longer risk being replayed.** Very slow
  turns (large attachments, long tool use, or slow approvals) are now
  budgeted end-to-end so they either finish cleanly or fail with a normal
  timeout — never a duplicated resend of a message that already went out.
- **Failed channel setup or attachment downloads no longer show sensitive
  details.** Error messages shown while setting up a channel, or when an
  attachment fails to download, previously could include internal
  credentials, tokens, or URLs. These now show only the type of failure.
- **Assorted smaller reliability fixes:** cleaner recovery from a channel
  that fails to connect, safer handling of Discord slash-command replies,
  and a fix for a legacy passkey/WebAuthn code path in some browsers that
  could fail to submit a credential during enrollment.

As part of this sweep, Sirius also tightened its safety net around sensitive
text: if something ever goes wrong while redacting sensitive content from
logs or saved conversation history, Sirius now blocks that output entirely
rather than risk showing unredacted text.

## Notes

- **Sparkle build version** is `116` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on `115` or earlier will offer this
  build.
- The signed core-runtime feed will be refreshed as `0.1.0-alpha.116` so the
  app, appcast, and runtime component remain release-synchronized.

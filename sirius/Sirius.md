<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius 0.1.8

## Sign in with a smart card in the browser

The built-in browser now supports CAC, PIV, and other compatible client
certificates. On a site that requests one, choose your certificate in the
macOS picker and enter your PIN if macOS asks. We tested CAC sign-in on
MyNavy Portal and Navy eHA in pre-release builds.

## Browser Use

- Paste tabular data into supported spreadsheets and embedded editors with
  native Paste. Sirius preserves the current selection so the editor can
  handle the paste.
- Hold keys or mouse buttons and run timed input sequences on interactive
  pages. Sirius can detect visible changes during a sequence even when the
  final view looks unchanged.
- Compatible pages can lock Sirius's browser pointer while your physical
  mouse stays free.
- Browser screenshots can give Sirius a short history of recent frames for
  comparison. Full viewport screenshots now use the same coordinates as
  the page.

## Messages and channel conversations

Messages now connects through the separate SiriusMsg app. Choose a chat
and workspace in SiriusMsg, then approve the connection in Sirius under
**Settings → Permissions & Security → Connected Apps**. Approve attachment
reading and sending reply files separately for each workspace. Previous
Messages conversations remain visible in Channels.

Channel conversations use the contact, space, channel, or thread name when
the provider supplies it. Supported incoming files appear on the message
that brought them in. A follow-up from the same sender in the same
conversation and thread can redirect a running turn while keeping work
Sirius has already completed.

## Questions, settings, and chat fixes

- Clarification questions open above the composer, one at a time. Submit
  from the question strip or answer in chat. When Sirius recognizes a chat
  reply as the answer, it marks the original question **Answered in chat**.
- **Permissions & Security** puts Connected Apps first and gives Tool
  Permissions, Activity, and On This Mac their own tabs.
- Recent images remain available to the model when you reopen a
  conversation. Memory and profile reminders let a text reply finish.
- Codex sessions now supply the session identity needed to reuse the
  conversation's prompt cache.

Requires macOS 26 or later on an Apple silicon Mac.

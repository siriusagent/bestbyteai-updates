<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius 0.1.7

## Find a result from earlier in your chat

Ask Sirius to find a term or result from your chat. If it only appeared in
a file read or terminal output, Sirius now checks the tool results from
that chat before looking in other chats. Open **Session search** in the
conversation to see the matching excerpt and the tool it came from.

Search, memory, and other tool details now open inline beneath the step
that produced them. Click the row again to collapse it. After a long
chat is condensed, Sirius checks the current chat’s history before
continuing the task.

## Recover interrupted work

If a connection drops while Sirius is waiting for the provider, it can
retry that request. If it still fails, **Connection failed** tells you what
happened and leaves completed tool steps visible. Review what already ran
before asking Sirius to continue. Use **Copy diagnostics** to report the
failure.

Sirius also retries an empty provider reply. If those attempts run out
during a Goal, the Goal shows **Goal stopped**. Use **Resume goal** to
continue the same Goal with its saved progress and limits.

- When a chat is open in two windows, both show the same Goal status and
  elapsed time. Closing the second window leaves the Goal running.
- The default time limit for a turn rises from 30 minutes to an hour.
  The default limit on model steps rises from 60 to 120.

## Open tools and side chats faster

Press **⌘T** to open Workspace Start. Click anywhere on the **Terminal**,
**DiffTree**, or **Temporary Chat** card to open that tab. You can also
open Temporary Chat directly from **File → Open Temporary Chat** or with
**⌃⌘T**. Reopening its tab brings back the draft until you end the
Temporary Chat.

## Browse privately in Temporary Chat

The browser in Temporary Chat is marked **Private browsing**. Cookies and
site data stay in memory for that chat. Favorites, Recents, and history
stay with your regular browser, and pages opened here are not added to
browser history.

When Sirius browses, reads a page, or takes a screenshot in Temporary
Chat, that work stays in this private browser. Closing the chat keeps
the page so you can reopen it. **End Temporary Chat** stops that browsing
and removes the temporary files Sirius created for those captures, page
reads, and document conversions. Downloads and files you save yourself
stay where you put them. If Temporary Chat is interrupted, Sirius removes
leftover temporary files the next time it starts.

## Dictate and listen on your Mac

- **Dictation** uses Whisper on your Mac and works offline after the model
  download. It reduces quiet background audio and skips stretches without
  detected speech, so Sirius is less likely to add words to your draft
  when you pause. If the model needs setup or repair, the microphone
  control links to **Settings → Voice**, where you can also add custom
  vocabulary.
- **Read Aloud** uses an on-device English voice for completed replies.
  The speaker menu lets you pause, resume, restart, or choose
  **Read All Text** to hear the code, tables, and equations in an answer.

## Read PDFs and view figures in chat

- PDFs reopen at a readable size in the built-in browser.
- When Sirius searches a PDF for a phrase, it checks the full extracted
  text and shows the page count, match count, and excerpts in the preview.
- Sirius retries PDF attachments that previously failed because of an
  outdated OCR setting.
- SiriusMarkdown 0.7.24 restores inline images from local files and keeps
  the opening text visible in collapsed messages that contain tall images.
  Mermaid flowcharts now render labels that contain semicolons.

## Browser and tool fixes

- In the built-in browser, moving your pointer elsewhere in Sirius no
  longer interrupts a drag the agent is holding. When browser actions
  repeatedly fail, Sirius can reassess its approach.
- Sirius can carry images returned by supported tools into later steps of
  the same turn, so it can refer back to what it saw.
- Sirius can read large skill instructions in sections when the full text
  exceeds the amount it can load at once.
- **Help → Share Feedback** keeps track of the chat you opened it from.

Requires macOS 26 or later on an Apple silicon Mac.

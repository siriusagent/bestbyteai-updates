<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius 0.1.8.19

This release restores in-app updates for Macs that could see 0.1.8.18 but were told they were already up to date. It includes the following changes from 0.1.8.18.

Sirius can now install updates when you quit, use its browser from connected messaging chats, and handle more of your Apple Mail and Messages work.

## Updates

- **Install updates automatically.** Turn on **Install updates automatically** in **Settings → General → Updates**. When an update is ready, Sirius saves pending work, installs on quit, and reopens. You can still check for and install updates on demand.
- Sirius sets up the matching Core Runtime after an app update. Runtime updates remain available through **Settings → Components**.

## Channels and chat collaboration

- **Browse from a connected channel with the chat closed.** Sirius can open pages and interact with websites in the background. Each conversation keeps its own tabs and website data. After inactivity, Sirius closes the browser window and restores the conversation’s tabs the next time it needs them.
- **Send notes to idle connected chats.** Messages between saved Sirius chats can appear in an idle connected conversation without starting a turn there. A running turn can pick up the message while it works. The transcript identifies the sending chat.
- With **SiriusMsg 0.2.0 build 28**, follow-up texts can steer an active Sirius turn or wait for the next turn. A message can still forward its usable text and files when one attachment is unsupported.
- Browser tools give clearer errors when a page requires a browser that is unavailable. Public search and supported document and caption lookups can still work in those cases.

## Messages and Apple Mail

- **Send PDFs and other attachments supported by Apple Messages.** Sirius preserves filenames and reports text submission and each attachment transfer separately. The report labels recipient delivery as unconfirmed when there is no delivery receipt.
- **Work across Apple Mail accounts.** List and search mailboxes and drafts, read a message and its attachment details, and save an attachment. Search results show which portions of the mailbox were scanned and where to continue.
- **Compose and organize mail.** Save drafts, send from a selected account, reply, and forward with attachments. Sirius checks the From address and the attachments Mail accepted. You can also move or archive mail, change flags, check for new mail, and sync an account. Send results reflect what Mail confirms.

## Browser, Reader, and chats

- Use eligible logins saved in Sirius Security Key for supported website sign-in requests. Sirius scopes the request to the site and tab, and hands off to you when the site requires verification.
- Sirius masks credentials in browser URLs in new tool results, reopened transcripts, and chat search previews.
- Bring Reader annotations into a chat draft. Pending history loads leave the current composer usable, and you can select another chat or start a new one while a history load is underway. Drafts continue saving when the database is busy.
- New interactive apps use Mac-inspired layout and icon defaults. Saving an app to Library retains its state.
- Fixed file search results for paths that contain delimiter-like text. Background browser tabs also clear their tooltips when hidden.

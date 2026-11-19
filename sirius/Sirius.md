<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius 0.1.8.7

## Remote chat and approvals

- **A file can be the whole reply.** Ask for a PDF and Sirius can send the document without a caption. Telegram and Discord support file-only replies, and WhatsApp can now upload documents. File delivery also works when you reopen a channel conversation on your Mac.
- **Keep chatting after an approval.** A database lock could leave a conversation stuck after a failed turn. You can now follow up in the same thread.
- **Review requests are easier to read.** Telegram and WhatsApp show a **Review request** button. Discord and Google Chat show a labeled link. Each request includes the action, a six-character comparison code, and its expiry.
- **See where your file went.** Google Chat, SMS, and IRC tell you when a file is saved in the Sirius conversation. If Sirius cannot confirm an upload, it tells you and keeps the attachment available.

## Memory and conversation history

- **Find a detail across chats.** When a history search turns up more than fits in one result, Sirius keeps dated excerpts from different conversations and can reopen the original messages. A follow-up search can recover a person or occasion you named, even when the first search left it out.
- Memory search gives more weight to distinctive words, project names, and filenames. Saved facts rank ahead of chat recaps, and a long entry can return the passage that matched. Sirius can also report when it finds no supporting evidence.
- After a long conversation is condensed, Sirius can look back through its messages and tool results to recover details such as the contents of an earlier file read.
- Similar notes can stay separate. Sirius rejects proposed merges that lose details such as dates or addresses. Automatic deletion based on age and lack of use is off by default. Deleting a chat removes its recap and preserves facts you saved separately. If a profile update skips a section, Sirius identifies it.

## Browser Use

- Sirius now sees page text and a numbered outline of controls. Toolbar buttons, selections, checkboxes, expanded menus, and help text have clearer labels. Duplicate tooltips collapse, while separate actions in the same row remain individually selectable.
- After a click, Sirius retains the name of the original control even if the page redraws. If an action times out, it can tell whether input was sent and whether it observed the result.
- Vision-capable models can see the current viewport alongside the controls after opening, inspecting, or interacting with a supported page. Sensitive-input screens retain their capture protections.

## Files and conversation display

- **Play audio and video in DiffTree.** Workspace media opens in a native player, including files above the text-preview size limit. Play, pause, seek, or take video full screen. Playback stops when you switch files or hide DiffTree.
- **The sidebar respects your choice.** If you reopen it while using DiffTree in a narrow window, it stays open until you hide it.
- **Prices render correctly in chat.** Dollar amounts retain their dollar signs, spacing, and bold formatting while a reply streams and after it finishes. This release includes SiriusMarkdown 0.7.25.

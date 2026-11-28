<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius 0.1.8.23 · Build 264

This release brings chat activity, more precise notifications, and live subagent corrections to Sirius. The matching Core Runtime also includes the conversation and prompt-cache fixes delivered in Core Runtime 0.1.8.22.1.

## Activity in chats

- Click the **Activity** button next to **+** in the title bar to see the current chat’s subagents, background tasks, files, links, and worktree changes. Sections show a preview and a count when more items are available. Choose the count to page through the full list.
- Subagent and task rows show their work status, including active work, failures, and items that need review. Open a row to inspect its conversation, task output, or exact file, link, or diff in the workspace.
- The transcript and composer stay aligned as Activity takes space. The chat scrollbar remains at the outer edge, and smaller windows place the card above the transcript.
- Opening a workspace tab makes room for its contents. Closing the workspace restores the Activity card at the same category and page. Diffs load when a project chat is reopened and open at the selected file and Git stage.

## Notification Center

- The sidebar bell updates as notices arrive and as they’re read. Notices are grouped by their source chat. The drawer offers new notices together while preserving your current reading position.
- Opening a notice switches to its owning chat and reveals the exact task, subagent run, or reply. A notice is marked read once its destination is visible. A newer notice remains unread if an older version was being opened.
- Reading or dismissing a notice leaves the work’s status intact. A failed task still appears as **Failed** in Activity, and a completed subagent still appears as **Done**.
- If a source is temporarily unavailable, the drawer keeps the last known notices and their read state. Source-specific actions become available again once Sirius can verify the destination.

## Live subagent corrections

- Sirius can start a collaborative subagent and send a correction through the worker that owns the run. Corrections target the selected conversation and run.
- **Codex:** Compatible App Server versions support steering the current turn. The bundled Codex client from ChatGPT was verified with `gpt-6.2-sol` when configured as the Codex executable.
- **Claude Code and Antigravity:** Supported read-only profiles can interrupt the current turn and continue with the correction in the same vendor conversation. Sirius records that continuation as a new run and keeps both runs visible in the child conversation.
- A delivery receipt reports provider acceptance separately from the child’s response. Queued, unsupported, stale, and unconfirmed corrections have distinct outcomes. A user Stop takes precedence over pending continuation.
- Subagent tabs follow the conversation across runs. Opening a notification for a particular run reveals that run’s history.

Live delivery depends on the installed vendor client and the selected profile. Profiles with custom CLI arguments use their regular execution path.

## Conversation continuity and prompt caching

- Resuming a chat restores its most recent compacted context and joins it to the messages added afterward. Long conversations retain the working context Sirius had before a restart.
- Gemini keeps earlier tool results stable when refreshing system context. Tool-schema guidance stays outside saved conversation history so routine tool availability changes create fewer avoidable changes to the reusable prompt prefix.
- These continuity fixes carry forward Core Runtime 0.1.8.22.1. Providers determine cache hits, and rates vary with the conversation and workload.

Requires macOS 26 or later on Apple silicon.

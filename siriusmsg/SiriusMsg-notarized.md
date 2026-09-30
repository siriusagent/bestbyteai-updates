<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# SiriusMsg 0.2.0 (build 17)

- Redesigned Chats, Connections, Activity, and Settings, with per-chat sharing and reply permissions, connection controls, and activity export.
- A chat is answered by exactly one connection. When two connected agents share a chat, SiriusMsg picks one, gives the message only to it, and moves the others past it, so nothing is replayed and two agents never answer the same text. Chats shows which connection answers and offers **Make primary** on the others; that choice is remembered until it goes stale.
- Polished search focus and clear controls, empty-state guidance, keyboard selection feedback, and button labels. Updated native icon packaging removes the gray surround while retaining the regenerated transparent artwork.
- Diagnostics distinguishes skipped checks from passing checks and reports clipboard failures. Manual chat entry preserves unsaved text on failure, and Add chats keeps the submitted selection stable while saving.
- Rotate aging authentication tokens in the app. Maintenance warnings show the actual age and recommended threshold without calling a working token expired. Rotation verifies new local connections, refreshes health, and preserves existing authenticated connections.
- Enabled VM token exports refresh after rotation. Export failures are reported separately; guest-held copies still need secure replacement before reconnecting.
- Added structured health and remediation details for clients, plus file-backed credential reload on reconnect in the Python and TypeScript SDKs.
- Added agent connection setup and a bundled signed MCP helper. Rich-action requests preserve chat permissions, exact message targeting, and unconfirmed dispatch status.
- Added opt-in native reactions, threaded replies, edits, unsends, effects and typing with SIP enabled. Availability follows saved feature permissions and current Mac access checks.
- Added managed typing during reply preparation in Kit, Python and TypeScript. Typing is advisory: failures do not suppress agent work or discard replies, and delivery retains its own confirmation and safety checks.
- Updated SwiftPython to 0.7.0-preview.1.1, including the commercial Python runtime and matching public API reference.
- Fixed chat permission keyboard focus, failure recovery for permission saves and activity export, cancellation during media staging, and rich-operation ownership across service restarts.
- Improved long-message and nested-reply selection, including exact thread-root checks and recovery from transient Messages animations. Timed-out native sends reconcile against the read-only Messages store without sending again.
- Fixed Chats so removing access removes the conversation even when Messages reports it under an equivalent identifier form, and so the picker no longer offers a chat that is already shared.
- Fixed native actions on a reply inside a thread: reactions, edits, and unsends bind the exact thread root, and the reply overlay closes after a confirmed edit, unsend, or reaction instead of staying open.
- Fixed long-message binding on Macs that use a 24-hour clock or a language other than English.
- Fixed the Python and TypeScript clients so a full-size protocol response is read instead of failing, and so an unterminated frame is rejected instead of buffering without a limit.
- Fixed a slow Codex start being reported as an unanswered turn. Bringing the connection up now has its own deadline, separate from the reply deadline, so a process that is still starting is never described as Codex failing to respond.
- Fixed the send-operation ledger so a request that failed before dispatch can be retried with the same operation ID, and documented how to recover if the ledger fills.
- Fixed the agent's control socket so a client that connects and never sends its request, or never reads the reply, is closed after a short deadline instead of stalling the agent.
- Bounded SiriusMsg-owned storage: delivered attachments are released when their message is acknowledged and deleted shortly after, nothing is kept longer than seven days without a redelivery, Codex staging keeps only its most recent media within a byte budget, and completed Codex turn receipts are collected after thirty days. Original files in Messages are untouched.
- SiriusMsg Help now includes cropped screenshots of the Chats access controls, the Add chats sheet, a connection's access and totals, and the Activity filters.

Known limitation: recipient-visible typing dots remain unreliable; the Typing indicators control is disabled. Naming a waiting agent in the message text is not a way to reach it — the connection that is not answering takes over a shared chat by being made primary. The accepted canary passes the other exercised message and media flows. Full sleep/wake and installed login-item recovery certification remains separate from that canary result.

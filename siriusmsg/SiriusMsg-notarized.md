<!-- sparkle-sign-warning:
IMPORTANT: This file is signed into the Sparkle appcast. Any modifications require re-running generate_appcast or sign_update before publishing.
-->
# SiriusMsg 0.0.1 (build 12)

Apple Messages history and agent integration update.

## Added

- Added authenticated chat listing, history reads, and message search for chats
  explicitly allowed in the SiriusMsg app.
- Added a native MCP server and SiriusMsg plugin for ChatGPT and Codex with
  focused health, allowed-chat, history, search, and send tools.
- Added durable send operation identifiers so a reconnect or service restart
  can return the existing result without dispatching the same message twice.

## Changed

- Extended the Swift client and generated Python and TypeScript SDKs with the
  new history operations and recoverable send-operation errors.
- Bounded history pages, search work, archived-body allocation, individual
  message text, and aggregate response text.
- Kept Messages database reads and Automation inside the signed SiriusMsg agent;
  the MCP plugin connects through the authenticated local service.

## Verification

- Generated SDK drift check: passed.
- Swift test suite: 367 tests passed.
- Python SDK lint, format, and 13 tests: passed.
- TypeScript SDK format, build, and 14 tests: passed.
- 12,000-row Messages Store WAL stress test: passed.
- Source and staged plugin validation: passed.
- Signed bundle integrity and bundled Python runtime verification: passed.
- App and DMG notarization: accepted by Apple notary service.
- Gatekeeper, DMG image, stapling, and Sparkle signature verification: passed.

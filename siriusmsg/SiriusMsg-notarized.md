<!-- sparkle-sign-warning:
IMPORTANT: This file is signed into the Sparkle appcast. Any modifications require re-running generate_appcast or sign_update before publishing.
-->
# SiriusMsg 0.0.1 (build 9)

Maintenance release that removes the inactive recipe surface, strengthens
privileged bridge and durable-queue boundaries, and reduces recurring Store,
socket, and SwiftPython worker overhead.

## Changed

- Removed the Recipes app surface and agent recipe runtime. The legacy reload
  command remains Codable for one release and is rejected explicitly so older
  clients fail cleanly instead of activating a hidden second automation path.
- Preserved the existing public protocol version, read-only Messages Store,
  explicit allowlists, ScriptingBridge send path, and sanitized adapter
  envelopes.

## Fixed

- Fenced durable adapter decisions, replies, retries, and terminal queue updates
  by lease owner so a paused worker cannot act on a job after another queue
  handle reclaims its expired lease.
- Rejected denied outbound attachment sends before reading or staging the source
  file, and enforced attachment size policy before allocation and throughout the
  read to cover concurrently growing files.
- Closed every accepted service connection during shutdown, including
  authenticated non-subscriber sockets, and rejected protocol work once the
  service is stopped.
- Rolled first-enable cursor state back when allowlist persistence fails so a
  rejected configuration update cannot alter later replay behavior.

## Performance

- Replaced one-byte-at-a-time Service and Kit protocol reads with buffered 16 KiB
  framing while preserving multiple-frame, CRLF, EOF, and 1 MiB-limit behavior.
- Serialized Kit writes so concurrent ACK and request traffic cannot interleave
  bytes on one socket.
- Filtered outbound rows in SQL, deferred attachment lookup until after
  allowlist/cursor/message checks, chunked attachment queries in bounded batches,
  and replaced full-history cursor materialization with a grouped metadata-only
  aggregate.
- Sized the SwiftPython process pool from the one active protocol-v1 adapter
  instead of inactive configurations, and made hosted adapter test-pool teardown
  deterministic.

## Verification

- Generated SDK drift check: passed.
- Swift test suite: 290 tests passed.
- Python SDK tests: passed.
- TypeScript SDK build and tests: passed.
- 12,000-row Messages Store WAL stress test: passed.
- Unsigned Xcode app/agent build: passed.
- App notarization: accepted by Apple notary service.
- DMG notarization: accepted by Apple notary service.
- Gatekeeper: accepted as Notarized Developer ID.
- DMG image verification: valid.
- Signed bundle verification: nested agent bundles `Python.framework`,
  `SiriusMsgHooks.framework`, and `SwiftPythonWorker` without Homebrew,
  user-home, checkout, private source, bytecode cache, or global
  `site-packages` linkage.
- Operational validation gate: passed with the notarized DMG path.

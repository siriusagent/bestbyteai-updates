<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.030

Alpha.030 puts session permissions directly in the composer and strengthens
Native Computer Use targeting, paste, verification, and diagnostics.

## Switch session permissions from the composer

- Choose Auto, Strict, Read Only, or Permissive without leaving the current
  conversation.
- The selection hot-applies to the focused session only. Settings remains the
  persisted default for new conversations and other sessions.
- The pill reports the worker-confirmed preset, shows progress while the live
  context updates, and retains the previous confirmed state if an update fails.
- Compact layouts keep an accessible icon-only selector instead of widening or
  restructuring the conversation columns.

Permissive is the widest ordinary baseline, not unrestricted access. Dangerous
bash, sensitive files, nondelegable authority, and other human-only boundaries
remain enforced. Ask mode remains an independent read-only tool filter.

## More precise Native Computer Use

- `computer_use_paste` inserts multiline or TSV content with one bounded paste
  into the exact target. Sirius restores the prior clipboard only when a newer
  user copy would not be overwritten, and payload contents never enter logs or
  replay receipts.
- Exact-window activation verifies that the requested window owns keyboard
  focus. A frontmost app with the wrong sibling window selected no longer
  borrows a false success, and minimized or other-Space targets refuse quickly.
- Press, type, and paste verification now stays inside the keyboard-focus
  region. Unrelated live-region refreshes cannot falsely confirm the action.
- Typed gate conditions validate their required fields before any mutation,
  and role-only element gates can publish a fresh reusable target for later
  action-set steps.
- Declared regions can confirm sparse semantic changes when a downsampled pixel
  probe misses the real update, while pixel evidence remains primary.
- Replay protection now distinguishes replacing writes from compounding text
  insertion and preserves current references across a fully proven no-op
  activation.
- Each mutation emits one redacted structured outcome for diagnosis without
  logging typed or pasted payloads, clipboard contents, window titles, menu
  paths, or element labels.

## Reliability fixes

- Closing a stable named window now resolves its owning process before
  dispatch, even when only the bundle and window ID were supplied.
- Action-set aliases for unnamed controls re-resolve through the same unique
  role rule as direct selectors instead of failing as semantically empty.

## Verification

- Non-slow Python gate: 7,839 tests passed with 28 skips and 12 deselections.
- Full Swift host gate: 3,650 XCTest cases passed with 22 skips, plus 13 Swift
  Testing cases.
- Focused composer-permission and Computer Use regression suites passed.
- Changed-file Ruff, generated-wiki drift, and whitespace audits passed.

Sirius Computer Use remains experimental. It uses the SwiftPython worker and
native-host architecture: the Python agent plans and calls typed tools while
the signed Swift host owns macOS observation, input, authority, and
verification.

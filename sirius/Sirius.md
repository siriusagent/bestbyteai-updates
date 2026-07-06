<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.110

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This release ships a one-PR polish pass of the right-panel terminal: dead
banner buttons now work, the terminal tracks the directory you `cd` into,
and the standard macOS terminal affordances (clear, font zoom, tab cycling,
scroll-to-bottom, find options) are finally wired up. It also fixes a hang
in the Ollama Compatible Model Hub download modal.

## What's new

- **Ollama model pull no longer hangs on cancel / network stall.** The
  Compatible Model Hub download modal could stick on "Cancelling…"
  indefinitely. The Python downloader now bounds the `httpx.stream` read
  timeout (`connect=30s, read=120s`) so a network stall surfaces as a
  terminal "failed" frame instead of wedging the worker, and the Swift
  cancel sheet stops polling and dismisses immediately instead of waiting
  for a terminal frame that may never arrive.
- **Banner buttons do something.** The sticky terminal banner's action
  button was an empty closure, so every sandbox banner action — "Retry",
  "Download image", "Build image", "Re-download image", "Rebuild image",
  "View kmsg tail" — did nothing. A real action identity now backs each
  label, a button renders only when a handler is actually wired, and every
  sticky / per-tab banner is dismissible. Sandbox image banners deep-link
  into Permissions & Security; "Retry" reopens the sandbox; "View kmsg tail"
  expands the crash detail inline.
- **The terminal now knows where you are.** OSC 633 `P;Cwd` and OSC 7
  `file://host/path` cwd reports now flow into the tab's working directory.
  Previously they were parsed and thrown away, so the command-gutter hover
  card showed a stale directory and a Stop → restart shell reopened in the
  wrong place. This also fixes a pre-existing parser bug: the standard
  `P;Cwd=<value>` (equals) form the Sirius shell-integration scripts emit
  was never parsed — only the semicolon form was. Both forms now parse.
- **Live tab titles.** Shell-reported titles (OSC 0/2) now drive the tab
  label for user host tabs, falling back to the current directory's
  basename, then the static title. Agent-attached tabs keep their
  bridge-derived identity titles so ownership never depends on a mutable
  display string.
- **Running indicator.** The tab strip now shows an accent dot while a
  command is active (the `commandRunning` field was a dead value no code
  ever set; it now mirrors the command log).
- **Clicked links open.** `http(s)` URLs in scrollback now open in the
  system default browser (xterm's web-links addon was posting them; the
  Swift host was dropping them).
- **Cmd-K clears the terminal.** Display-only — it rewrites the visible
  buffer via the existing replay path and leaves the raw buffer and any
  in-flight command capture untouched, so a running capture resolves
  identically before and after a clear.
- **Cmd-Plus / Minus / 0 font zoom.** A session-scoped delta layered on top
  of the appearance preference; never persisted, reset by Cmd-0 and on
  relaunch. Zoom resizes the PTY rows/columns correctly.
- **Tab cycling.** Ctrl-Tab / Ctrl-Shift-Tab and Cmd-Shift-] / Cmd-Shift-[
  switch tabs (wrapping). The new shortcuts only fire when the terminal
  owns key focus, so they never shadow the composer or other panes.
- **Scroll-to-bottom pill.** While you're scrolled up during a stream, a
  glass pill appears; clicking it jumps back to the bottom.
- **Find options.** The find bar gains case-sensitive / whole-word /
  regular-expression toggles. An invalid regex reports "No results"
  instead of throwing.
- **Tab context menu** (Restart Shell, Copy Working Directory, Interrupt,
  Close, Close Others) and an empty-state "New Terminal" action.
- **Tab strip polish.** Hover-reveal close buttons, design-token
  compliance (no hard-coded view-site numbers), and accessibility labels
  reading title, kind, and running state.
- Retired the unused `onSelection` bridge message that shipped the full
  selection string across the WebKit boundary on every drag.

## Notes

- **All work is in the Swift host** (`swift/ui/`). No Python engine,
  bridge, capture, redaction, or kill-verification changes — the new tab
  actions (Restart, Close Others, Clear) reuse the existing cancel /
  rotate paths. `TerminalKillVerificationTests` passes unmodified.
- **Sparkle build version** is `110` (`CFBundleVersion`). Apps on `109`
  or earlier will offer this build.
- **Test coverage:** new `TerminalPanelPolishTests` (27 cases) cover
  banner actions / dismissal, live cwd (OSC 633 equals + semicolon, OSC 7),
  shell titles, running state, clear, tab cycling / close-others / restart,
  find options, scroll state, the link scheme guard, the OSC 633 parser
  fix, the web-seam JS surface, and `objectWillChange` publish regression
  for the new tab mutations. The terminal suite (133 tests across
  `TerminalGridLayoutTests`, `TerminalKillVerificationTests`,
  `TerminalSidebarPlanTests`, `TerminalPanelPolishTests`) passes
  consistently; full package suite is 2415 tests.

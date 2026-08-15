<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.022

Alpha.022 gives long-running work two native control surfaces: a durable
background-task manager in the status bar and a compact Goal control panel with
truthful generated-output budgets. It also stabilizes provider prompt-cache
reuse and contains a native crash path in parallel web-page extraction.

## Background tasks

- **Background work is visible and controllable from one native manager.** The
  status-bar popover separates active, attention, and recent tasks; advances
  elapsed time without inventing state; opens the exact retained Terminal when
  available; and otherwise shows bounded redacted output.
- **Actions report what actually happened.** Stop sends one graceful interrupt
  and never auto-escalates. Force Quit is distinct and confirmed. Remove Stale
  is available only when the runtime proves no live target remains. Durable,
  idempotent receipts keep signal acceptance, verified death, task
  reconciliation, agent wake, and acknowledgement separate.
- **SQLite is the sole background-task authority (BUG-431).** Legacy JSON is
  imported once and retained only as a diagnostic backup. Concurrent workers,
  origin ownership, coherent snapshots, watches, receipts, and events no
  longer depend on last-writer JSON state.
- **Terminal ownership survives the hard cases.** Actions route by exact
  session/generation before colliding local SIDs (BUG-432), cancelling capture
  is no longer treated as verified process death (BUG-433), and closing a
  background-owned tab detaches the UI without terminating its command
  (BUG-434). Worker replacement, session switching, duplicate windows, and
  closed-tab output fallback preserve the same authority.

## Goal control and budgeting

- **Goal budgets now measure generated output.** Provider-reported output is
  the allowance; input, cache, call-count, current-context, and cumulative
  Session usage remain separate diagnostics. Missing terminal metering halts
  safely instead of becoming a zero-cost continuation path.
- **The Goal popover uses compact progressive disclosure.** Latest Work,
  current context, efficiency details, output/time safeguards, and the actions
  that are valid for the exact Goal state are visible without rewriting live
  limits from Settings.
- **Continuation is explicit.** Manual continuation adds a bounded output
  tranche. Paused Resume preserves current limits, while extending a hard
  output or active-time limit requires its own typed, revision-checked action.
  End and Clear remain distinct and confirmed.
- **Wrap-up preserves terminal truth.** Completion, pause, budget, and
  iteration summaries retry only safe pre-content transient failures and do
  not replay the Goal mutation.

## Providers and web extraction

- **Prompt caching now follows Sirius's stable-prefix boundary (BUG-429).**
  Anthropic and Claude-through-OpenRouter cache the byte-identical stable
  system prefix separately from volatile memory, time, Plan, and Goal state.
  OpenRouter also receives a non-owning session-scoped affinity key. Prompts,
  tools, permissions, reasoning replay, lifecycle, and provider ownership are
  unchanged.
- **Parallel host-backed `web_read` is contained (BUG-430).** Rendered WebKit
  captures no longer enter the Trafilatura/lxml/htmldate path that could kill a
  session worker. Host captures use safe HTML parsing; the remaining CLI/no-host
  extraction is serialized and carries start/finish telemetry for recovery.

## Verification status

- The final tree passed 7,782 Python tests with 23 skips. The non-slow Python
  gate passed 7,775 tests with 17 skips and 13 deselections.
- The native suite passed 3,327 XCTest entries plus all 13 Swift Testing cases.
- The signed isolated background-manager release matrix passed all 16 required
  scenarios, including ignored-SIGINT Force Quit, cross-session routing,
  closed-tab retention, worker replacement, duplicate-window read-only state,
  migration, and fail-closed busy/corrupt/newer-schema stores. Keyboard,
  VoiceOver, motion, contrast, text-size, density, nested-signature, and orphan
  checks also passed.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 147 with the matching signed core-runtime feed.

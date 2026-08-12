<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.021

Alpha.021 makes the native Terminal feel like one continuous Sirius workspace:
each live task retains its own renderer, streamed bytes and command state remain
correct under sustained output, and the terminal follows the app's appearance
without spending a second row on duplicated status. It also tightens Auto's
model-facing denial boundary and fixes Gemini schema compatibility.

## Changed

- **Terminal chrome is compact and native (BUG-413).** The selected tab uses a
  tonal shape, Host/Sandbox creation shares one menu, and cwd remains available
  from the tab tooltip, context menu, and VoiceOver label without a permanent
  cwd/“ready” strip.
- **Terminal appearance follows Sirius by default.** Fresh and reset settings
  use Match App with typed opaque light/dark palettes. Explicit Sirius and
  Always Dark choices are preserved.

## Fixed

- **Live tasks cannot reuse or race another task's terminal renderer
  (BUG-410).** Each coordinator owns one retained WebView. Serialized
  workspace/tab/generation keys fence replay, append, theme, decoration, find,
  scroll, and callback work while background PTYs and session routing continue.
- **Completed commands no longer stay visually running during a sustained
  stream (BUG-411).** Status, exit code, and duration update immediately;
  expensive row re-anchoring remains bounded and coalesced.
- **Split PTY reads no longer corrupt valid Unicode (BUG-412).** Box drawing,
  block characters, emoji, and other multibyte UTF-8 survive arbitrary transport
  chunk boundaries; genuinely malformed or truncated bytes still repair safely.
- **Auto denials no longer expose internal policy machinery to the acting model
  (BUG-414).** The result is `Blocked: <bounded explanation>` when useful
  optional prose exists, or `Blocked.` otherwise. Authority basis, semantic
  boundary, retry state, and audit metadata remain internal, and freeform
  explanations are not persisted in authority history.
- **Gemini tool schemas no longer include unsupported `dependentRequired`
  keywords (BUG-415).** Conversion remains recursive and does not mutate the
  source schema.

## Verification status

- The reconciled permission, engine, security, and session slice passed 610
  tests. Changed-file Ruff, generated-wiki drift, and diff whitespace checks
  are clean.
- Terminal ownership, generation fencing, command-status, UTF-8 streaming,
  appearance, accessibility, and Gemini schema regressions are covered by the
  native and provider test suites.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 146 with the matching signed core-runtime feed.

<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.118

**Strict pre-release unstable build.** This alpha is for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This is a significant reliability and capability release. It expands Sirius's
native macOS computer-use stack, makes model-call performance measurable
without recording user content, and replaces the transcript's most expensive
streaming and layout paths. It also carries the latest SiriusMarkdown crash and
long-document fixes.

## What's new

- **Sirius can complete more desktop tasks as one precise native action.** The
  agent can now activate an exact app, close an exact named window, select an
  exact menu path, press an exact named control, type into a field and submit,
  or quit an app through bounded Swift-host transactions. Exact matching blocks
  ambiguous targets before mutation, and the shipping app—not the CLI—owns the
  execution path.
- **Desktop actions report what actually happened.** Computer use now
  distinguishes verified, unconfirmed, blocked, and failed effects instead of
  treating a delivered input event as success. App quit is conservative: it
  verifies process exit, refuses unknown or destructive save dialogs, and uses
  force termination only when explicitly requested.
- **Performance diagnostics can attribute individual model calls without
  storing their content.** Sirius now records provider/model identity, timing,
  call counts, and token usage while excluding prompts, tool arguments,
  credentials, and results.

## Faster and more stable transcripts

- **Long live responses no longer progressively beachball the app.** Each
  transcript row now keeps one persistent, manually framed AppKit host; sealed
  history is isolated from mutable-tail layout, and asynchronous row-height
  updates no longer force synchronous `NSHostingView` measurement loops.
- **Streaming updates paint on a real 33 ms cadence without invalidating the
  whole window.** The event ledger now wakes the cursor-based transcript pump
  through a dedicated append signal, while SiriusMarkdown performs bounded
  source mapping, parsing, highlighting, and preparation away from the main
  actor. Tables, math, Mermaid, syntax highlighting, and source-backed
  selection remain enabled.
- **The JavaScriptCore streamed-code crash is fixed.** SiriusMarkdown 0.6.16
  roots retained JavaScript functions, arguments, and results during
  incremental Highlight.js and Mermaid work, preventing the
  `JSC::JSRopeString::resolveToBuffer` use-after-free seen while a code fence was
  still growing.
- **DiffTree and Plan Document Markdown use Sirius's bounded selection path.**
  These surfaces no longer fall back to per-block AppKit text views that could
  stall or crash on long lists and block quotes.

## Computer-use refinements

- Window discovery now defaults to user-facing windows while preserving an
  explicit complete inventory with filtering reasons.
- Exact named targets are resolved before mutation, and menu/type-and-submit
  workflows verify each stage without retrying an inconclusive mutation.
- OpenAI OAuth/Codex requests use a stable model-scoped prompt-cache key when
  caching is enabled and no explicit key is supplied, reducing avoidable
  repeated prompt work.

## Notes

- **Sparkle build version** is `118` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `117` or earlier will offer
  this release.
- The signed core-runtime feed is refreshed as `0.1.0-alpha.118` so the app,
  appcast, and Python runtime component remain release-synchronized.

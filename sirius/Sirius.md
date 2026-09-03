<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.035

Alpha.035 makes background work inspectable, simplifies the Terminal, and
replaces the old bug-report form with a useful local-first feedback workflow.

## Background Tasks is now a real right panel

- Click the status-bar background-task indicator to open a dismissible panel
  that matches the Terminal's tabs and chrome. There is no extra toolbar icon.
- Each task gets a read-only tab whose redacted output streams while the task
  runs. Refresh, Copy, Stop, Open in Terminal, Force Quit, and Remove Stale
  Record are available in the same panel.
- Closing the panel never affects the task. Destructive confirmations remain
  bound to the exact task you selected even if another task finishes while the
  dialog is open.

## Terminal is cleaner

- The unused command gutter, status glyphs, hover cards, and overview markers
  are gone, giving terminal output the full panel width and symmetric padding.
- Command capture and history, keyboard navigation, and the native right-click
  menu are unchanged.

## Share Feedback produces reports worth acting on

- A new native intake covers bugs, bad results, good results, safety checks,
  performance, and other feedback with one clear description field and
  explicit evidence controls.
- Bug investigations can reconstruct bounded session facts about model calls,
  tools, timing, errors, mutations, and replay state. The resulting report can
  include impact, metrics, a timeline, causal chain, severity and confidence,
  negative findings, remediation, acceptance tests, unresolved questions, and
  an evidence index.
- Positive feedback is prepared locally without provider analysis. Every flow
  shows the provider boundary before analysis and sends nothing until you
  explicitly choose a destination.
- Review is editable and shows the exact selectable Markdown payload. Privacy
  options control whether a report remains local or may be copied, emailed, or
  sent to GitHub.
- Auto-saved report bundles track every review and privacy edit atomically.
  Finder reveal verifies the report bytes, revision, policy, and SHA-256 digest
  and fails closed instead of opening stale output.

## Privacy behavior is more useful

- Final replies no longer replace ordinary phone numbers and email addresses
  with generic PII markers.
- Registered secrets, credentials, SSNs, payment cards, and credential-shaped
  tokens remain scrubbed. Logs, transcript persistence, tools, memory, and
  diagnostics keep the stricter redaction policy.

## Everything from Alpha.034 remains

The macOS 26.5 launch repair, stable Browser AutoFill toolbar action,
Credentials & Access pane, protected Keychain support, and component update
discovery all ship unchanged.

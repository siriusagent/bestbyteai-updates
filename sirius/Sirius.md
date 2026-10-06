<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.038

Alpha.038 improves the transcript and document panels and introduces Sirius's approved robot icon.

## Transcript and documents

- Replies use the published SiriusMarkdown 0.7.2 renderer for native Markdown and rich content.
- File links open the Reader beside the conversation. Related files remain in session-owned tabs.
- Reader and DiffTree share document navigation and source presentation, including Find and heading links.
- File navigation, syntax, and file-type icons are consistent across panels.
- Attached images resolve within their owning session and align with the user message.
- Tool results have bounded previews; full output remains accessible. Short tool narration avoids unnecessary padding.
- The redundant transcript footer is removed, and document scroll restoration avoids feedback loops.

## Runtime

- Uses the published SwiftPython 0.7.0-preview.1.2 runtime with its matched worker and framework contracts.
- Updates the signed core runtime alongside the app, including prompt, session, and tool-result changes.
- Invalid tool narration stays suppressed through redaction, approval, and persistence without changing tool execution.

## Icon

- Sirius uses the approved chevron-and-dash robot portrait, with its original shell detail preserved.
- The Dock icon and OAuth success image use the same approved artwork.

Requires macOS 26 or later on Apple silicon.

<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.46

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixes a packaged-app crash when Markdown math rendering loads SwiftMath fonts;
  SiriusMarkdown now guards the unsafe packaged-app SwiftMath entry path and
  falls back safely instead of entering SwiftPM's generated `Bundle.module`
  accessor.
- Fixes missing-workspace recovery so stale project roots show
  `Workspace Missing`, Git/worktree actions are gated until a real folder is
  selected, and folder recovery starts at the nearest existing parent.
- Fixes CLI-agent npm installs so user-scoped Node/npm paths survive the native
  administrator fallback and install failures surface useful npm/AppleScript
  output.
- Hardens file mutation permissions so `write_file`, `edit_file`, and
  `notebook_edit` canonicalize relative paths, traversal, symlink aliases, and
  macOS `/private/etc` aliases before bypass/permissive modes can allow
  sensitive paths.
- Carries alpha.45 provider replay, forced-tool UI, browser media, and release
  signing fixes forward.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

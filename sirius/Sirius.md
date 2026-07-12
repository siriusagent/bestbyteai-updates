<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.117

**Strict pre-release unstable build.** This hotfix is not an RC, production
release, compatibility promise, or support boundary.

## Fixed

- **The DiffTree Markdown preview and inline Plan Document artifacts no
  longer freeze or crash Sirius.** Both surfaces could silently fall back to
  SiriusMarkdown's bounded AppKit text-selection view instead of Sirius's own
  cross-block selector. On long documents with lists or block quotes, that
  view's per-layout-pass cost could peg the main thread for 30+ seconds and,
  in rare cases, crash through an AppKit constraint-update guard — the cause
  of the alpha.116 hang and crash some users saw. Both surfaces now pin the
  same selection strategy the transcript already used, and the underlying
  SiriusMarkdown dependency is updated to fix the same class of issue at its
  source for any host.

- **New sessions start once, even if the control is clicked repeatedly.** Sirius
  now treats fresh-session startup as a single transition and disables its New
  Session controls until that transition completes. Deferred memory reflection
  also stays on its background drainer instead of occupying worker 1's callback
  command lane, preventing the reflection-worker respawn seen on alpha.116.

- **Opening or updating composer popovers no longer crashes Sirius.** On
  macOS 26, AppKit could dereference a null callback while animating a popover
  window resize. This was most visible when the new context-usage breakdown
  finished loading, and the same system failure could affect the provider and
  model picker while its contents changed. Sirius now forces those dynamic
  popover updates to resize without animation, avoiding the crashing AppKit
  path.

## Notes

- **Sparkle build version** is `117` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `116` or earlier become
  eligible only after the operator resumes and publishes this hotfix.
- When the rollout resumes, the signed core-runtime feed must be refreshed as
  `0.1.0-alpha.117` so the app, appcast, and runtime component are published in
  sync.

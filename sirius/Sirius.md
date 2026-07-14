<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.120

**Strict pre-release unstable build.** This alpha is for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This is a focused hotfix over alpha.119. Completed inline tools now publish
their terminal visual state and result content immediately.

## Immediate inline tool completion

- **Tool status symbols leave the running state as soon as the result lands.**
  Successful tools turn green and failed tools turn red without waiting for a
  later tool call or the assistant's final response to repaint the transcript.
- **Result-backed detail arrives in the same update.** Inline action popovers
  and web-search drawers populate from the terminal result immediately while
  preserving their stable disclosure and row-host identity.
- **The fix applies across the shared inline-tool pipeline.** It covers skills,
  file operations, search, MCP, browser, computer-use, and other tools routed
  through inline annotations; it is not special-cased to `skill_use`.
- **Regression coverage exercises the real persistent host.** Generic success
  and failure, web-search success and failure, stable-ID semantic mutation, and
  the mounted AppKit row refresh are pinned by focused tests and the full Swift
  suite.

## Notes

- **Sparkle build version** is `120` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `119` or earlier will offer
  this release.
- The signed core-runtime feed is refreshed as `0.1.0-alpha.120` so the app,
  appcast, and Python runtime component remain release-synchronized.

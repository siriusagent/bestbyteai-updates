<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.121

**Strict pre-release unstable build.** This alpha is for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This hotfix rollup keeps browser input on the browser, repairs Decision Request
submission and multiline input, adds native reasoning controls for supported
Ollama models, and makes an installed core-runtime update actionable without a
manual quit and relaunch.

## Ollama reasoning controls

- **Supported local and cloud tags expose their native choices.** Sirius checks
  each exact model's live `/api/show` capability metadata. Most thinking models
  offer Off/On; GPT-OSS offers its required Low/Medium/High levels.
- **The choice reaches Ollama's native chat API.** The saved selection is sent
  as top-level `think`, with real JSON booleans for Off/On and level strings for
  GPT-OSS. Models without live thinking metadata remain usable without a
  speculative selector.

## Browser action ownership and targeting

- **Trusted browser paste stays in WebKit.** A browser-owned paste operation no
  longer falls through to the Sirius composer when the web view owns focus.
- **Modal and coordinate verification is more exact.** Controls inside an
  existing modal can verify from durable action evidence, while a newly
  appearing error modal still fails closed. Context-menu and native AutoFill
  placement now account for flipped WebKit coordinates and page zoom.
- **AutoFill remains native.** Sirius forwards current field focus and viewport
  geometry to the browser coordinator, then invokes the macOS/WebKit AutoFill
  surface rather than storing or synthesizing credentials.

## Decision Request input

- **Submit is live from the card's first render.** Decision Request rows no
  longer retain a missing callback when the request arrives before the turn's
  terminal event.
- **The text field has predictable keyboard behavior.** Return submits;
  Shift-Return and Option-Return insert a newline. Long answers wrap and grow
  through five visible lines before scrolling.

## Core runtime relaunch

- **Components now includes a Relaunch action for the installed core runtime.**
  Sirius schedules the exact running app bundle to reopen after the current
  process exits, then follows the normal termination path so live sessions and
  the SwiftPython worker pool drain before updated runtime workers start.
- **Damaged or missing runtimes still fail closed.** Relaunch is unavailable
  until Install or Repair produces a usable core runtime.

## Notes

- **Sparkle build version** is `121` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `120` or earlier will offer
  this release.
- The signed core-runtime feed is refreshed as `0.1.0-alpha.121` so the app,
  appcast, and Python runtime component remain release-synchronized.

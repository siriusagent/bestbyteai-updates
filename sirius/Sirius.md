<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.111

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This release fixes a crash when rendering inline LaTeX math on macOS 26.5.x,
adds Save PDF to Downloads in the embedded browser, stops permission metadata
from leaking into MCP tool arguments, and tightens credential-gated command
matching.

## What's new

- **Fixed a crash when rendering inline LaTeX math on macOS 26.5.x.** On
  macOS 26.5.x, inline math in messages could trap the app. Native LaTeX
  math now renders reliably again in installed builds.
- **Save PDF to Downloads from the embedded browser.** A new "Save PDF to
  Downloads…" menu item saves the PDF currently displayed in the browser tab
  straight to your Downloads folder. It saves what's already on screen rather
  than re-fetching the URL, so it works for PDFs reached through logged-in or
  popup-mediated flows even after a session token has expired.
- **MCP tool calls no longer leak permission metadata to remote servers.**
  Internal audit and prompt metadata attached to permission decisions is now
  carried separately from the arguments sent to MCP servers. This fixes
  "invalid params: unexpected additional properties" rejections from MCP
  servers with strict schemas.
- **Tighter credential-gated command matching.** The `command_names`
  credential list is now scoped to dedicated credentialed CLIs, and matching
  now warns when it hits a generic interpreter or HTTP client that could
  accidentally gate unrelated commands. Channel secrets are also scrubbed
  from logs.

## Notes

- **Sparkle build version** is `111` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on `110` or earlier will offer this
  build.
- The math-render fix is a dependency update; no Python engine or UI-shell
  changes were needed for it.

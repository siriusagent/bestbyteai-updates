<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.9

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Updates the embedded SwiftPython runtime dependency to
  `swiftpython-commercial` `0.5.9`, picking up the corrected macOS
  resource-pressure spawn gate for low-memory hosts.
- Publishes a new signed core runtime archive so Python-side MCP changes are
  available through the update feed, not only through a freshly installed DMG.
- Switches MCP OAuth setup to a Swift-owned loopback redirect session before
  launching the browser, avoiding custom-scheme callback crashes and making the
  callback URI match the Python-side OAuth request.
- Keeps the alpha.8 boot deadline and low-memory two-worker cap, so startup
  failures continue to surface as retryable boot errors instead of permanent
  "Starting engine..." hangs.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

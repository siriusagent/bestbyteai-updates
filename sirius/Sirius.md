<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.64

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Long diagnosis replies render through SiriusMarkdown's production path.**
  The transcript now uses SiriusMarkdown 0.5.8's CoreText-painted prepared-line
  renderer instead of the older native-line compatibility fallback, reducing
  SwiftUI text work during long streaming Markdown replies.
- **The SiriusMarkdown integration contract is locked to the 0.5.8 API.**
  Policy tests now assert the remote `0.5.8` dependency and the production
  renderer mode so future transcript changes do not regress to the slower
  fallback path.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

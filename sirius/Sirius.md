<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.65

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Channel provider packages are included in the public runtime.** Telegram,
  Discord, WhatsApp, SMS/Telnyx, Google Chat, and IRC dependencies now ship in
  the signed core-runtime feed, and Settings marks older runtimes repair-needed
  instead of healthy when those imports are missing.
- **Customer-installed component wheels load correctly.** The embedded Python
  launchers now carry the Python-host hardened-runtime exceptions needed for
  native `.so`/`.dylib` wheels installed from Settings.
- **SiriusMarkdown is updated to 0.5.9.** The app bundle resolves the current
  public renderer package for transcript, plan, and Markdown preview surfaces.
- **Release gates now block this class of miss.** The build and release
  verifiers smoke-test channel imports, require channel roots in the signed
  runtime archive, check embedded Python launcher entitlements, and prune
  unused Google API discovery documents from the runtime archive.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

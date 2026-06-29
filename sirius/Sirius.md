<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.92

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **The channel catalog is now exposed as a versioned snapshot for the Settings
  UI.** `channel_catalog_snapshot()` exports a JSON-safe, versioned description
  of the channel catalog so the SwiftUI Channels surface consumes static
  provider/field metadata directly, without round-tripping sensitive values.
  The Swift UI now builds provider configuration sheets from
  `ChannelDescriptorSnapshot`, and catalog loading errors are surfaced in the
  Channels settings view instead of failing silently.
- **Channel field Keychain membership is documented and enforced consistently.**
  `ChannelField` clarifies that a field's `kind` describes its editor shape
  while persistence as a secret is decided by membership in `secret_fields`,
  so provider config sheets no longer leak or mis-classify Keychain-backed
  fields.
- **Browser panel autofill, context menu, and page print are hardened.** The
  Browser content view, coordinator, tab model, and JS bridge gained
  autofill-source guarding, a richer context menu model, and a page-print
  bridge, with the autofill source guard preventing synthetic form fills from
  untrusted page sources.
- **Direct-provider brand icons are unified across the shell and Settings.**
  Provider logo shapes were refreshed so branded provider icons render
  consistently in the channel/provider surfaces.
- **The bundled Python core runtime refreshes with this build.** The signed
  core-runtime feed ships the latest `sirius_agent` package, including channel
  catalog snapshot support and provider/runtime-rebind fixes from the prior
  alpha.91 cycle.
- **The distributable build defaults now target alpha.92 / build 92.**

## Distribution

- Published as monotonic Sparkle build 92.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

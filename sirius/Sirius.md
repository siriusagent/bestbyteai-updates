<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.11

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Updates SiriusMarkdown to `0.5.5` so installed app bundles no longer crash
  during HighlightJS or Mermaid resource preparation when SwiftPM's generated
  resource-bundle accessor cannot resolve the package bundle.
- Hardens the signed-bundle release gate so the app cannot ship without the
  SiriusMarkdown HighlightJS/Mermaid resources, the SiriusUI resource bundle,
  or the SwiftMath font bundle.
- Tightens the signed core-runtime feed gate: generated manifests now carry a
  `runtimeInputSHA256`, release verification validates the detached manifest
  signature, rejects stale or unsafe runtime archives, and can compare against
  the last shipped runtime digest or signed manifest.
- Improves GitHub CLI discovery and Settings behavior by checking user-local
  `gh` installs before system fallbacks, bounding non-interactive command
  waits, clearing stale capability/status state, and documenting the same
  discovery order for workers.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

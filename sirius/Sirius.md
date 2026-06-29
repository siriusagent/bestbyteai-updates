<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.94

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This is a **hotfix** over alpha.93. It repairs web search failover and routes
channel (service-worker) web capture through the Sirius.app Research tab.

## Changes

- **Explicit-engine web search now fails over on browser/capture failures.**
  When `web_search` is called with an explicit `engine` (google, ddg, brave)
  and that engine's browser/SERP capture fails, the tool now tries the
  remaining supported engines instead of hard-erroring. A genuine
  zero-result SERP on the *requested* engine is still honored as a valid
  empty answer — only capture/browser failures fall over.
- **Channel replies now use the Swift-hosted web capture path.** Generic
  service-worker channel turns no longer pass through `build_session`, so
  they previously dropped to the Python browser fallback for
  `web_search`/`web_read`. The service worker now carries a real
  `LoopConfig` with the host-owned `web_capture_provider`, and that config
  is refreshed when channel settings or the persistent snapshot change.
- **Research capture falls back to the default coordinator for unknown
  sessions.** `BrowserHostBridge` now resolves the Research-tab coordinator
  for unrecognized session IDs (e.g. channel sessions) against the shared
  default coordinator, so background channel web capture lands in the
  Research tab instead of failing with `noCoordinator`.
- **The bundled Python core runtime refreshes with this build.** The signed
  core-runtime feed ships the updated `sirius_agent` package, including the
  web search failover and service-channel web capture routing from this
  hotfix.
- **The distributable build defaults now target alpha.94 / build 94.**

## Distribution

- Published as monotonic Sparkle build 94.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

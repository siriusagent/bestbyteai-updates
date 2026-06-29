<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.91

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Channel provider startups retry transient connect failures.** Provider
  connect now uses a bounded retry policy for network, TLS, and timeout
  failures before marking a provider degraded, so a brief blip during startup
  no longer permanently disables an otherwise healthy channel.
- **Channel status reports surface startup errors without hiding healthy
  providers.** `ChannelManager` tracks per-provider startup failures and
  includes them in the status report, so degraded providers are visible
  without obscuring providers that connected successfully.
- **Channel runtime rebinding refreshes service dependencies.** `ChannelBridge`
  and `ChannelHost` gained `rebind_runtime_dependencies` so worker respawns
  and runtime refreshes re-wire channel services instead of leaving stale
  handles behind.
- **Channels Settings documents the startup-error status path.** The Settings
  UI and operator docs now describe how degraded provider startup errors appear
  in the Channels surface.
- **The distributable build defaults now target alpha.91 / build 91.**

## Distribution

- Published as monotonic Sparkle build 91.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

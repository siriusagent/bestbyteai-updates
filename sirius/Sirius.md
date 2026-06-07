<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.21

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixes a service-worker scheduling race that could make Context & Memory
  knowledge-base rebuilds fail while background channel event polling was
  active.
- Serializes service-worker maintenance and settings calls, including memory
  maintenance, cron, channels, GitHub, keychain prime, and credential refresh,
  so worker-0 control-plane actions do not overlap each other.
- Keeps the channel event poller active, but makes it wait behind any in-flight
  maintenance action instead of submitting another worker command at the same
  time.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

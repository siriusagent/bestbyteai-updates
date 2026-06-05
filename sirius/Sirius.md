<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.8

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Updates the embedded SwiftPython runtime dependency to `swiftpython-commercial`
  `0.5.8`, picking up the host resource-pressure gating fix for worker pool
  startup.
- Adds a 60 second startup deadline around the post-pool worker runtime bind.
  If binding stalls, Sirius now cancels the boot attempt, shuts down the partial
  worker pool, and surfaces a retryable boot error instead of staying at
  "Starting engine...".
- Caps low-memory hosts under 12 GiB physical RAM at two workers to reduce
  first-boot pressure on 8 GiB Macs.
- Adds boot telemetry for warmup, bridge pre-bind, runtime bind, timeout, and
  cleanup phases without logging secrets or config payloads.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key and update feed are enabled for alpha update testing.

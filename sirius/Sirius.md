<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.72

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Fixes

- **MCP server credentials are safer and more predictable.** Sirius now
  preserves bearer, header, and OAuth binding state through persistent config
  round trips, worker runtime setup, probes, and per-session diagnostics instead
  of dropping or flattening credential-backed server configuration.
- **MCP setup failures are clearer in the app.** The MCP Tools & Skills
  settings UI now surfaces authentication and probe details more directly,
  including better handling for authorization-required states and protected
  values.
- **Tool-call transcript rows render richer MCP details.** Inline tool
  annotations now keep MCP server/source context, argument summaries, and error
  details together so failed calls are easier to inspect without losing the
  compact transcript layout.
- **Channel turns keep their context in sandboxed dispatch.** Session dispatch
  now forwards available channel context into the sandbox decision path, fixing
  a bug where sandbox-policy injection tests could fail once channel context was
  absent or stale.

## Distribution

- Published as monotonic Sparkle build 72.
- Ships a refreshed signed core-runtime feed for the MCP credential, probe,
  transcript, and dispatch fixes.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.76

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Browser automation is more resilient and less chatty.** The `browser_use_*`
  tooling gained an ergonomics layer driven by a real field report:
  `browser_use_open` auto-recovers from a torn-down default tab via one bounded
  retry on a fresh agent-owned tab (explicit `tab_id` / `use_selected` are never
  re-routed); `browser_use_eval` is now snapshot-independent and is never failed
  by the stale-snapshot gate, while ref-based verbs still fail honestly;
  composite-widget descriptors carry value authority so a lagging input value no
  longer produces a false-negative verification; repeated full element lists are
  summarized and diffed (state changes are never elided, sensitive windows always
  degrade to empty); high-entropy framework class hashes are dropped while
  human-readable classes and documented hooks are preserved; and overlay
  probe/dismiss nudges only fire when the needed control is plausibly covered.
- **The iMessage channel surfaces SiriusMsg capabilities and recipe runtime.**
  The channel hero now renders a capability matrix and recipe-runtime section, and
  the embedded SiriusMsg dependency is updated to `0.0.1-alpha.11`.
- **The distributable build defaults now target alpha.76/build 76.**

## Distribution

- Published as monotonic Sparkle build 76.
- Ships a refreshed signed core-runtime feed for the browser ergonomics changes.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

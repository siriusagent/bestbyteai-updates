<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.33

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Adds the Permissions & Security authority center, giving credentials, wallet
  policy, tool rules, remembered bash approvals, macOS automation access, and
  recent authority decisions a single settings surface.
- Makes permission presets enforce their advertised behavior more closely:
  readonly now blocks stateful browser open/mutation calls, strict still asks
  before remembered bash overrides, and auto/default honor exact remembered
  command approvals after deny/ask safety gates.
- Tightens remembered approval handling so prompt responses can only persist
  authority for the tool and command that actually triggered the approval.
  Wallet payments stay per-payment, credential setup stays explicit, and
  ineffective remembered choices are hidden or downgraded to approve-once.
- Adds a local authority audit path for permission, credential, and wallet
  decisions, with URL-shaped arguments redacted from stored audit details.
- Improves wallet and credential tool rendering and test coverage around
  broker approvals, execute-dag propagation, and authority payload delivery.
- Fixes an installed-app crash in the DiffTree Git Graph empty state by avoiding
  SwiftPM's generated `Bundle.module` resource accessor in runtime UI paths.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.73

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Fixes

- **Wallet status reports Coinbase CDP token balances identified only by
  contract address.** On Base mainnet, `wallet_status` can now display USDC
  rows that the provider returns without `token.symbol` or `token.name`; the
  parser matches the configured network contract address instead of treating
  the balance as missing.
- **Native ETH balance matching is more robust.** CDP rows using the EIP-7528
  native ETH address now match the gas/native balance path even when text token
  labels are absent.
- **SiriusMarkdown is updated to 0.5.11.** The app bundle picks up the
  published generated bare-TeX recovery and SwiftMath normalization fixes for
  transcript, plan, and DiffTree Markdown rendering.

## Distribution

- Published as monotonic Sparkle build 73.
- Ships a refreshed signed core-runtime feed for the CDP wallet status fix.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

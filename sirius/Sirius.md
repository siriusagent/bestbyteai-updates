<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.74

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Fixes

- **Wallet status follows paginated Coinbase CDP token balances.** Base mainnet
  wallets with enough unrelated token rows to push USDC off the first CDP page
  now continue through `next_page_token`, so Wallets & Payments and
  `wallet_status` can report the configured USDC balance instead of
  `balance unknown`.

## Changes

- **The macOS terminal command gutter now uses native hover and menu
  affordances.** Command decorations render themed status glyphs with
  overview-ruler marks, native hover cards, and an AppKit command menu.

## Distribution

- Published as monotonic Sparkle build 74.
- Ships a refreshed signed core-runtime feed for the CDP wallet status fix.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.90

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Direct provider brand icons ship as real logos.** The four direct
  OpenAI-compatible providers introduced in alpha.89 — DeepSeek, Moonshot
  Kimi, Z.AI GLM, and xAI Grok — now render branded marks in the Network &
  Providers library, the provider detail-sheet header, and the composer
  assistant avatar, replacing the generic SF Symbol placeholders
  (`brain.head.profile`, `moon.stars.fill`, `z.square.fill`,
  `x.square.fill`).
  - **DeepSeek** and **Moonshot AI** come from the vendored
    `simple-icons` submodule, bumped to upstream `16.24.1` so the
    `deepseek` and `moonshotai` marks are on disk.
  - **Z.AI** and **xAI (Grok)** are not carried by simple-icons upstream;
    their 24×24 monochrome marks come from
    [lobehub/lobe-icons](https://github.com/lobehub/lobe-icons) and
    template-tint identically to the simple-icons glyphs.
  - All four inline SVG strings through the existing template-render path
    (`NSImage.isTemplate = true`), so they inherit the foreground color in
    every surface. No asset catalog or SPM resource is introduced, so the
    `Bundle.module` icon-crash class (BUG-209/211/230/241) cannot recur.
- **The distributable build defaults now target alpha.90 / build 90.**

## Distribution

- Published as monotonic Sparkle build 90.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

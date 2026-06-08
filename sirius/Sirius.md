<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.32

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Adds the `dynamic_ui` presentation tool for structured transcript visuals:
  bar, line, scatter, donut/pie, table, metric grid, and timeline components.
  The renderer normalizes common model-shaped payloads, rejects unsupported
  chart kinds instead of silently changing them, and keeps bounded markdown
  fallbacks for copy/search/render-failure paths.
- Polishes Dynamic UI charts for professional transcript use. Donut charts now
  render with center totals, compact value/percent legends, duplicate-label
  aggregation, largest-slice caps, and long-tail grouping. Bar, line, and
  scatter plots use the available mobile card height, compact unit-aware labels,
  and accessible SVG labels.
- Makes wide Dynamic UI tables usable in chat by preserving readable column
  widths, keeping the first column sticky while horizontally scrolling, and
  avoiding wrapped fragments in professional report-style tables.
- Improves metric grids with explicit positive/negative/neutral delta tones and
  separate caption rows so explanatory notes are not dropped.
- Fixes Gemini tool-schema normalization for providers that reject JSON Schema
  `type` arrays by converting nullable type arrays into scalar `type` plus
  `nullable`.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

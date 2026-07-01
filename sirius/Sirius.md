<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.100

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This is a **hotfix release** over alpha.99. It fixes the silent coordinate-drop
footgun in `computer_use_click` and clarifies how to click surfaces that the
AX tree cannot represent.

## Changes

- **`computer_use_click` is explicitly dual-mode and mutually exclusive.**
  Passing both `ref` and `x`/`y` is now rejected early with a
  `conflicting_click_targets` reason (both on the Python tool boundary and in
  the Swift host runner) instead of silently dropping the coordinates — the
  footgun that made canvas clicks look impossible. The model gets an actionable
  reason and drops one input rather than concluding it cannot click.
- **Click tool description and `delivery` enum.** The `click` entry now spells
  out the two modes (AX press by `ref` vs. raw coordinate click by `x`/`y` with
  no `ref`) and adds a `delivery` option (`pid` vs. `hid`) for coordinate
  clicks. When a `pid`-targeted coordinate click no-ops on a canvas, retrying
  with `delivery: "hid"` injects a hardware-level click (a momentary cursor
  warp).
- **`action_not_available` points at the coordinate form.** When a resolved
  element advertises no clickable primary (e.g. a window that only offers
  `AXRaise`, or a static canvas container), the result now carries
  `recommended_next_actions` directing the model to
  `computer_use_click with x + y and NO ref` instead of letting it conclude the
  surface is unclickable.
- **`verify_via_screenshot_recommended` hint on unconfirmed coordinate clicks.**
  A coordinate click or drag whose AX-tree (and window) diff comes back empty
  is still honestly reported as `unconfirmed`, but now carries a warning that AX
  verification is blind on schematic/vector/game canvases — the model should
  re-observe with a screenshot to judge the outcome. The hint never upgrades
  the `unconfirmed` verdict.
- **Regression coverage expanded.** Python and Swift tests pin the
  `conflicting_click_targets` rejection, the `recommended_next_actions` payload,
  and the `verify_via_screenshot_recommended` warning path.
- **The distributable build defaults now target alpha.100 / build 100.**

## Distribution

- Published as monotonic Sparkle build 100.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

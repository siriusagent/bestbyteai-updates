<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.004

**Alpha channel release.** Sirius's core product surfaces and signed update
path are stable enough for regular use. The alpha label remains a pre-1.0
release channel — updates may still refine behavior and compatibility — but
this is a user release, not an installation or packaging test.

This release adds a private delivery tier for Computer Use mouse/keyboard
input that closes a class of "click reports success but the app silently
rejected it" failures in Chromium/WebKit surfaces, fixes a menu-matching gap
against ellipsis glyphs, lets a stale accessibility ref self-heal instead of
always blocking, and fixes a crash in the Browser's Turnstile-challenge
Accessibility scan.

## Computer Use: SkyLight delivery, menu matching, and stale-ref self-heal

- **Mouse/keyboard delivery gains a private SkyLight tier
  (`ComputerSkyLightBridge`), additive to the existing public `postToPid`
  path.** The public `CGEvent.postToPid` used by `type`/`press`/`scroll`/
  coordinate `click`/`drag` skips WindowServer's `CGSTickleActivityMonitor`
  activity tickle, which some Chromium/WebKit renderer surfaces treat as a
  signal that the synthetic event is untrusted and silently drop — even
  though the API call itself reports success. This was caught with
  photographic proof: a WebKit `<input type=color>` swatch whose native
  color panel never opened after an `AXPress`-delivered click.
  `ComputerSkyLightBridge` resolves the private `SLEventPostToPid` SPI once
  and posts through it *in addition to*, never instead of, the existing
  public call. When the private symbol is unavailable, every affected call
  degrades silently to exactly its pre-SkyLight behavior — no new failure
  mode. No cursor warp, no foreground steal; a successful attempt is
  surfaced via a new `skylight_delivery_attempted` warning.
- **`computer_use_select_menu_item` matches an ellipsis glyph against three
  ASCII periods.** Menu-path resolution now tries an exact title match
  first and, only when that yields zero candidates, falls back to the same
  punctuation-folded comparison element-label resolution already trusts —
  still requiring exactly one candidate before proceeding. Concretely:
  Microsoft Excel renders `"Go To..."` with three ASCII periods, but a
  model turn requesting `"Go To…"` (single glyph) used to block even
  though `available_titles` showed the obvious match.
- **A stale ref self-heals by live re-identification instead of always
  blocking.** `computer_use_click_element`, `computer_use_type`,
  `computer_use_set_value`, and `computer_use_perform_secondary_action`
  used to hard-block with `stale_ref` the moment a cached ref drifted from
  a fresh accessibility read — even when the exact same control was still
  uniquely identifiable live (common right after `launch_app`/
  `activate_app` repositions a window). The host now attempts one live,
  ambiguity-safe re-identification by exact (role, label) before failing
  closed; a healed call's `pre_action_ref_validation` reports
  `"stale_healed"` rather than being folded into `"stable"`.

## Fixed

- **An off-main Turnstile Accessibility scan crashed with a MainActor
  isolation trap.** The Browser's Cloudflare Turnstile checkbox scan
  (`BrowserTurnstileAXScanner.scan(_:)`) walked through
  `NSHostingView.accessibilityHitTest`, which must evaluate the
  MainActor-isolated SwiftUI accessibility node graph; running that walk
  from `Task.detached` tripped Swift 6's runtime isolation check and
  crashed with `SIGTRAP`. The scan now runs synchronously on the main
  actor, matching the always-on Accessibility snapshot path's
  already-proven pattern. (BUG-368)

## Changed

- **SiriusMarkdown bumped to `0.6.21`.** Invalidates a provisional
  streaming-region height the package could cache before a settled
  descendant relayout finished at a new width. Signed Sirius validation
  shows this is not yet sufficient inside Sirius's bounded persistent
  transcript row host: a finalized reply can still be clipped above its
  action row after narrowing the conversation column. (BUG-367 remains
  open pending a package-level fix.)

## Notes

- **Sparkle build version** is `129` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `128` or earlier will offer
  this release.
- **No Sirius Python runtime changes** shipped in this release; the signed
  core-runtime feed remains `0.1.1-alpha.003` and is unchanged.

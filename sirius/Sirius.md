<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.001

**Alpha channel release.** Sirius's core product surfaces and signed update
path are stable enough for regular use. The alpha label remains a pre-1.0
release channel — updates may still refine behavior and compatibility — but
this is a user release, not an installation or packaging test.

This release teaches in-app browser automation to absorb common real-world
friction — CAPTCHA checkboxes, proof-of-work walls, Cloudflare's Turnstile
challenge, and blocking overlays — on its own instead of stalling out, renders
richer native Markdown on both sides of the conversation (your sent messages
now included), lets the model narrate its own tool activity instead of
generic status labels, and fixes a table-streaming stutter and a rate-limit
banner that misdescribed a system recovery attempt as a rejected model
change.

## Browser automation absorbs more friction on its own

- **The reCAPTCHA v2 "I'm not a robot" checkbox is now a single-click
  carve-out, on by default.** A real browser waits through the JS wall and
  clicks the checkbox once — it self-terminates into a `captcha` gate the
  moment an image-grid challenge appears or the click doesn't resolve
  cleanly; it never attempts to solve one. Discoverable and toggleable from a
  new **Browser** card in Settings → Tools; the existing
  `SIRIUS_BROWSER_V2_CHECKBOX_CLICK` env var still overrides it for
  headless/advanced setups.
- **Cloudflare Turnstile / Managed Challenge is now recognized and waited
  out.** Cloudflare has moved industry-wide from the classic full-page
  "checking your browser" interstitial to Turnstile, which Sirius previously
  had no vocabulary for. A wait-only carve-out (no click, no solving) now
  recognizes Cloudflare's current "Verify you are human" copy and lets the
  browser clear it the same honest way as the existing proof-of-work wait.
- **A blocking overlay no longer costs a full round-trip to clear.** When a
  click, type, or similar action is blocked as covered by an overlay, Sirius
  now auto-attempts one safe dismissal and retries the original action inside
  the same tool call. Payment, subscribe/purchase, and CAPTCHA overlays are
  never auto-dismissed, and a failed or unsafe attempt still reports the
  honest blocked result.
- **A 403/429/451 that shows up mid-action is now caught, not just at the
  initial page load.** The browser panel forwards the latest HTTP response
  status into every action, so a denial that occurs partway through a
  sequence gates honestly instead of silently reporting success against a
  page that actually rejected the request.
- **`browser_use_probe_reachability` no longer requires a `snapshot_id`.** It
  now defaults to the tab's current snapshot — useful right after an overlay
  block, where the model has the control it tried to act on but not
  necessarily a snapshot ID for it.
- Friction telemetry (proof-of-work waits, checkbox clicks, Turnstile) is
  now recorded as structural-only counters with no URL, page text, or
  challenge content, so how often these carve-outs actually help is
  measurable.

## Richer Markdown on both sides of the conversation

- **Your own sent Markdown now renders in the user bubble too.** Headings,
  emphasis, lists, quotes, links, code, tables, math, and sanitized native HTML
  use the same renderer and safety policy as assistant Markdown without
  changing the exact source that is sent, copied, edited, or retried. Short
  prose and compact HTML content-hug; layout-heavy content uses a readable
  finite width; long rich sends show a larger, softly faded preview and a quiet
  leading Show more control. VoiceOver only traverses that bounded preview
  while collapsed and gets the complete structured content after expansion.
- **Markdown responses now render more of what a provider actually sends,
  natively.** Sirius pins SiriusMarkdown `0.6.19` and lets its native HTML
  policy handle provider-authored headings, tables, lists, anchors,
  formatting, code, and subscript/superscript — no WebView, no new
  surface. Transcript, plan artifacts, and DiffTree previews keep the
  original Markdown source, automatic link decoration, and favicon
  resolution; remote images stay explicitly blocked as before.
- **Streaming Markdown tables no longer visibly thrash.** Generating a table
  used to make the transcript jump and reflow on nearly every row — table
  rows and dotted text were slipping past the transcript's 33 ms coalescing
  window, and each partial cell was rebuilding the whole grid's layout.
  Table rows now publish only through the last complete row per cadence
  tick, with the unfinished row held until it's whole. (BUG-359)
- **A narrow table's wrapped last line could bleed across the row divider
  below it — fixed.** A row that only needed two lines at first measure but
  wrapped to three once its final width settled could get cached at the
  shorter height, letting that third line paint through the next divider.
  SiriusMarkdown `0.6.19` resolves each row's minimum height for its actual
  width before caching it, covering assistant, user-bubble, plan, and
  DiffTree Markdown alike with no app-side workaround. (BUG-361)
- **Composer and transcript text now scale independently, and transcript
  code is a touch larger.** The composer input has its own typography
  separate from assistant prose and user bubbles, and transcript code blocks
  default to `12pt` instead of `11pt` for better readability.

## Tool activity narrates itself, in the model's own words

- **Every tool call and think step now describes what it's doing, in the
  model's own words.** Instead of a generic "Thinking…" or "Searching the
  web…" label, the one-line narration next to each tool's activity in the
  transcript is now written by the model itself for that specific call —
  selected once when the call starts and never rewritten by the result.
  It's kept strictly separate from the tool's actual arguments: it never
  reaches a handler, an MCP server, or any permission/security check. If
  it's ever missing (an older session, a noncompliant provider), Sirius
  falls back to its previous deterministic summary — execution is
  unaffected either way, and it's never treated as proof anything actually
  succeeded.
- **Channel status updates now show that same authored sentence.** Discord,
  Telegram, and Google Chat's edited-in-place status message, and WhatsApp's
  single typing acknowledgment, now mirror exactly what the transcript
  shows instead of an independent, generic phase vocabulary.
- **Approval prompts read more like what the agent is actually about to
  do.** When a tool call needs your sign-off — a permission prompt, a
  credential/API-key request, or a wallet/payment approval — the summary
  line at the top now uses the same authored sentence when the model
  provided one, falling back to the existing mechanical summary otherwise.
  Everything that actually matters for the decision — the risk badge,
  credential/wallet details, policy explanation, and the Approve/Deny
  controls themselves — is untouched; only the headline sentence changes,
  and it never affects what gets approved.

## Fewer support surprises from the agent loop

- **`tool_search` now stays available through error backoff and
  browser/computer recovery instead of going dark with the tool it's
  containing.** Previously, once a tool tripped error backoff or a
  browser/computer-use family was fully contained for the rest of a turn,
  `tool_search` itself got hidden along with it, cutting off the model's
  only path back to any other tool. It now stays callable and correctly
  reports the contained names as blocked.
- **Sirius's own rate-limit recovery no longer shows up as a rejected model
  change you never asked for.** When an automatic attempt to switch a
  429'd chat back to your default provider had nowhere to fall back to, or
  the swap itself failed, it used to land on the same banner reserved for a
  model change *you* picked from the chip — "Couldn't apply your model
  change" — even though you hadn't touched anything. A dedicated notice now
  names the rate-limited model and tells you what to do next. (BUG-360)
- **OpenRouter's Kimi K3 no longer fails before it starts streaming when a
  persona sets a repetition penalty.** OpenRouter advertises
  `frequency_penalty` support for `moonshotai/kimi-k3`, but the routed
  endpoint only accepts its zero default. Sirius now recognizes that
  specific 400, strips the field, retries before the first chunk, and
  remembers the constraint for later calls — without leaking it across model
  overrides. (BUG-358)
- **The model now gets full schemas for more of your tools per call.** The
  tool-surfacing "hot" tier default rose from 12 to 30, so fewer
  registered/enabled tools get routed through the cold-tier `tool_search`
  discovery path before the model can use them.

## Settings tuning

- **Memory and profile nudges are less chatty.** Both randomized turn
  intervals for the memory-write and profile-fact reminders now default to
  every 5–15 turns, up from 1–10.

## Notes

- **Idle-worker sheds now log their exact policy cause.** Sirius pins
  `swiftpython-commercial` `0.5.17` and records whether a shed came from an
  explicit call, a periodic memory/thermal/CPU snapshot, or Darwin
  system-memory pressure — closing the last diagnostic gap around
  monitor-driven sheds.
- **Sparkle build version** is `126` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `125` or earlier will offer
  this release.
- The signed core-runtime feed is refreshed as `0.1.1-alpha.001` so the app,
  appcast, and Python runtime component remain release-synchronized.

<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.028

Alpha.028 makes long browser work transactional and durable, carries
attachments through running-turn Steer, hardens provider catch-up across worker
replacement, and adopts SiriusMarkdown 0.6.26.

## Browser actions keep their identity and evidence

- **Compact observations now retain one snapshot lineage.** Paging reprojects
  the original descriptor universe instead of recapturing a moving page, and
  stale lineage fails explicitly.
- **Controls have stable semantic identity.** Generic control and collection
  context IDs keep state changes attached to the same target even when labels
  mutate.
- **Conditions remain target-scoped.** An identity mismatch is not a match,
  common text elsewhere on the page cannot satisfy an exact target condition,
  and target state, detachment, expansion, or popup evidence can settle the
  intended action without being overwritten by unrelated page drift.
- **Opaque frames remain safely actionable.** Rendered cross-origin frames stay
  visible as bounded pointer surfaces. Trusted keyboard input requires a fresh
  snapshot proving focus and never adds a speculative second click.

## Long research runs retain their proof

- New and selected tabs use the same bounded slow-JavaScript settlement as an
  ordinary navigation before returning their final controls.
- A page-created popup may close itself, but page script cannot close a tab
  created by Sirius or the user.
- Productive browser work no longer loses browser tools at an arbitrary call
  count. Semantic no-progress detection and non-retry-safe ambiguous-mutation
  handling remain active.

## Attachments work through Steer

- A running-turn Steer can carry images and documents, including an
  attachment-only follow-up. The pending transcript row owns and previews the
  original files while the staged manifest is validated and retained.
- Python slurps and bounds the attachment bytes before admission, then persists
  each accepted blob against the exact steered user row.
- Proven-safe normal-turn fallback transfers the same manifest. Uncertain
  delivery retains staging until the user explicitly sends again or dismisses
  it; skill chips remain unsupported rather than being flattened into text.

## Provider routing and session catch-up

- OpenAI-compatible routes can learn two precise pre-stream restrictions from
  an exact HTTP 400: automatic tool choice and one leading system message. The
  repair is provider/model-local, runs once, preserves instruction order, and
  keeps forced-tool requirements enforced locally.
- Persisted provider defaults no longer wake a dormant controller with a stale
  session handle after resource-pressure idle shedding. The next real dispatch
  rebuilds from the latest effective snapshot; live overrides revalidate and
  recover once against the replacement worker generation.

## SiriusMarkdown 0.6.26

- Sirius now resolves the public `0.6.26` tag at
  `1a7a03b00e446eed1dc277f5e284c4515c9db292`.
- Asynchronous globe-to-favicon replacement stays destination-correct and
  selectively reprepares only affected blocks.
- Authorized HTML `colspan` and `rowspan` participate in bounded native layout,
  borders, selection geometry, and width-specific measurement.
- Nested Markdown and authorized HTML containers retain native child blocks in
  source order through the same rendering, policy, overflow, copy, selection,
  and link-metadata paths.

## Verification

- SiriusMarkdown's 966-test product gate, visual probes, release CI, and fresh
  external SwiftPM consumer passed on the exact published commit.
- Focused browser suites cover retained lineage, target conditions, semantic
  diffs, tab ownership, slow-JavaScript settlement, opaque-frame focus, and 40
  productive browser decisions without a call ceiling. Signed live validation
  retained 42 inspectable proof tabs and saved a 14,860-character document in a
  focused opaque frame.
- Focused Steer coverage proves attachment-only admission, pre-admission byte
  retention, malformed-manifest rejection, exact-row persistence, and safe
  fallback. A signed isolated app completed a PDF-bearing interrupt-and-steer
  and persisted the 341,936-byte document on the accepted user row.
- Provider coverage reproduces both strict routed error dialects and exercises
  dormant-default deferral, next-dispatch rebuild, live-override recovery, and
  a signed idle-shed catch-up with no stale-handle worker command.
- The non-slow Python gate passed 7,724 tests with 28 skips and 12
  deselections. The full Swift host gate passed 3,411 XCTest cases with 21
  skips plus 13 Swift Testing cases. The focused SiriusMarkdown/user-bubble
  host gate passed 47 tests; Ruff, wiki drift, and whitespace audits passed.
- Signed-bundle integrity, app and DMG notarization/stapling, Gatekeeper,
  Sparkle/runtime signatures, and hosted-byte identity are hard publication
  gates for this release.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 153 with the matching signed core-runtime feed.

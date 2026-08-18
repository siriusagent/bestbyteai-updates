<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.027

Alpha.027 makes running-turn follow-ups dependable and makes provider and
background-task failures substantially easier to understand.

## Steer follow-ups stay in the conversation

- **Queued follow-ups appear immediately at the transcript tail.** Pending user
  bubbles replace the detached queue shelf and provide inline **Steer**,
  **Interrupt**, **Edit**, and **Delete** actions with accessible state copy.
- **Exact application proof keeps history honest.** Pending bubbles remain a
  presentation until the engine confirms the exact request identity; the same
  identity then becomes the durable user row without a blank or duplicate
  frame.
- **A turn ending is no longer a rejection.** Exact `turn_ended` evidence sends
  the unapplied text as the next normal message automatically. Only genuinely
  uncertain terminal delivery asks whether to **Send Again** or **Dismiss**,
  with an explicit duplicate-work warning.
- **Early clicks and mixed queue states recover correctly.** Steer waits for the
  exact duplex session to publish, and an uncertain row cannot block a later
  follow-up that is proven safe to send.

## Lossless provider diagnostics

- Provider errors preserve real HTTP status separately from exact symbolic
  codes, error types, routed upstream codes, request ids, `Retry-After`, and the
  original response body.
- Errors delivered inside an HTTP 200 stream retain status `0`; Sirius no longer
  invents HTTP 500 for values such as Codex `invalid_prompt`.
- Retry classification uses only documented, provider-specific contracts.
  Unknown values remain unknown and are not retried by guesswork.

## Background-task presentation

- Captured terminal output hides only empty outer rows while preserving
  interior whitespace and the complete redacted payload for **Copy**.
- Initial keyboard focus lands on actionable **Refresh** or **Back** controls
  instead of a static heading.

## Transcript and Markdown integrity

- A live assistant Markdown tail now stays mounted when it becomes final,
  removing the terminal seal remount and flicker.
- Cross-row transcript reflows preserve the first visible persistent row and
  its pixel offset while the reader is away from the bottom.
- One contiguous provider-authored Markdown run remains one parser document.
  Sirius no longer splits long fenced code, lists, HTML, math, or references at
  an arbitrary character threshold; native tool and plan insertions remain the
  real document boundaries.
- **Known limitation:** while one very long assistant row is still actively
  growing, reading near the top of that same row can remain visually jittery.
  Bottom-following and terminal sealing are smooth, but Alpha.027 does not
  claim the intra-row scroll-up case is solved.

## Verification

- Fifty-six focused Swift Steer tests pass, including controller-level proof
  that exact `turn_ended` rejection crosses terminal and starts the next turn.
- A signed isolated app completed normal Steer and interrupt-and-steer against a
  live running turn, and the revised terminal continuation was verified by hand.
- Provider, engine, factory, background-provider, native decoding, and
  background-manager tests cover the new diagnostic and presentation paths.
- The full Swift package run passed 3,389 XCTest cases with 20 skips and 13
  Swift Testing cases, including the transcript anchor, terminal projection,
  Markdown parser-boundary, and live/final parity regressions.
- Full host, Python, signed-bundle, notarization, Gatekeeper, and public-feed
  evidence is required before this release is marked shipped.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 152 with the matching signed core-runtime feed.

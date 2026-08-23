<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.029

Alpha.029 is a substantial native-automation release: it introduces bounded
Computer Use action sets, host-verified visual evidence and painted-text OCR,
first-class oMLX management, native vision routing, and safer Browser file and
dialog handling.

## Computer Use is experimental — and intentionally takes a different route

Sirius Computer Use remains **experimental**. It is built on the app's
SwiftPython architecture, but the responsibilities are deliberately split:
the agent loop and typed tools run in process-isolated SwiftPython workers,
while the signed Swift host performs macOS observation, input, authority, and
verification. That is a different route from the common screenshot-first
computer-use loop.

| Dimension | Common screenshot-first route | Sirius Alpha.029 route |
|---|---|---|
| Runtime boundary | A model returns mouse/keyboard actions to a browser, VM, or desktop executor. | A Python agent worker calls typed native-host callbacks through SwiftPython. |
| Perception | Repeated screenshots are the primary state. | Accessibility semantics come first; ScreenCaptureKit and Apple Vision OCR cover visual or painted surfaces. |
| Action targeting | Coordinates and keystrokes are usually the main contract. | Snapshot/capture-bound refs, exact app/window identity, AX actions, and explicit PID/HID fallbacks are separate contracts. |
| Verification | The next screenshot is commonly judged by the model. | The host evaluates declared postconditions across AX, window, pixel, visual, and requested OCR evidence, then returns ordered receipts. |
| Web apps | The desktop pointer path often drives the browser too. | DOM-backed sites prefer Sirius Browser Use; native Computer Use is the fallback for native or non-DOM surfaces. |
| Control | Environment policy surrounds the executor. | Per-session grants, sensitive-target blocks, FIFO mutation ownership, and user-interruption yield live in the macOS host. |

This is not a claim of universal application compatibility or benchmark
parity. Accessibility and Screen Recording permissions still matter, custom-
drawn Electron/Qt/OpenGL surfaces remain uneven, and an action without enough
evidence stays `unconfirmed` instead of being promoted to success. The KiCad
work behind this release also exposed a real limit: its wxWidgets/OpenGL canvas
accepts synthetic pointer input intermittently, and painted-grid keyboard
movement can be invisible to the anti-thrash guards.

## Native Computer Use gains evidence, composition, and safer control

- **One bounded action-set executor.** `computer_use_transaction` accepts up to
  16 typed steps / 12 mutations. Each step resolves against fresh state,
  dispatches at most once, records an ordered receipt, and requires a verified
  or explicitly satisfied gate before the next mutation. There is no rollback,
  resume, or blind replay.
- **Universal visual evidence.** Mutations attempt broker-owned before/after
  window captures with canonical pixel identities and exact identical/different
  relations. Inline-capable providers receive ordered unique post-state images;
  duplicate images collapse to references.
- **On-device painted-text OCR.** Apple's Vision recognizer extracts text and
  window-space boxes from explicit or descriptor-poor captures. OCR refs are a
  separate namespace, remain capture-bound, and never silently replace AX
  semantics or ambiently prove a mutation.
- **Declared postconditions.** Callers can state the intended effect; the host
  verifies it through scoped AX/window/pixel/requested-OCR channels instead of
  treating any screen change as success.
- **More honest input and recovery.** Capture-bound coordinates, pointer
  hit-test diagnostics, pid/HID delivery ladders, double-clicks, anchored
  scroll, cursor-move-before-click for crosshair surfaces, user-interruption
  yield, and verified-progress replay expiry reduce blind repetition.
- **Budget-safe desktop state.** Large app/window inventories now compact in
  valid JSON and disclose any final kept/total window cap.

## Local models and native vision

- **First-class keyless oMLX.** Sirius defaults to the local OpenAI-compatible
  endpoint, discovers the live roster, preserves hot-swap identity, and sends
  native VLM image blocks. The macOS settings pane manages model load/unload,
  tuning and downloads plus oMLX memory, scheduling, SSD cache, and admin
  sessions.
- **Ollama vision discovery.** Compatible Model Hub results include native
  Ollama Library vision packages and install them through Ollama's atomic pull
  path. Sirius continues to exclude raw Hugging Face vision imports whose
  auxiliary assets it cannot safely stage.
- **Provider-native image delivery.** Screenshots, browser frames, and image
  attachments become native image blocks on inline-capable routes. Non-inline
  providers retain the persisted `vision_analyze` fallback.

## Browser and workspace reliability

- Completed browser downloads return their real local destination in ordinary
  results. File selection is part of the same click/transaction action, and an
  agent-owned WebKit chooser fails closed instead of stranding a turn behind
  Finder; manual clicks still receive the native picker.
- JavaScript dialogs, camera/microphone prompts, and load failures use one
  Sirius-branded host-dialog family. Browser strategy checkpoints are soft
  reviews rather than tool-removal ceilings, while mutation replay safety stays
  hard.
- Browser authentication/WebAuthn telemetry is more precise, live session
  switching preserves composer ownership, and DiffTree operations remain
  rooted in the selected project/workspace snapshot.

## Verification

- Focused Computer Use, OCR, action-set, postcondition, visual-evidence,
  provider, Browser, session, and DiffTree regression suites cover the new
  contracts.
- The non-slow Python gate passed 7,817 tests with 28 skips and 12
  deselections. The full Swift host gate passed 3,619 XCTest cases with 22
  skips plus 13 Swift Testing cases.
- Changed-file Ruff, generated-wiki drift, and whitespace audits passed.
  Signed-bundle integrity, notarization/stapling, Gatekeeper, Sparkle/runtime
  signatures, and hosted-byte identity remain hard publication gates.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 154 with the matching signed core-runtime feed.

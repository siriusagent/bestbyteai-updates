<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.037

Alpha.037 is a reliability release across desktop control, the transcript, and
provider plumbing, plus an explicit policy for browser challenges.

## Desktop control that reports what it checked

- An action names the exact window it acted on by binding rather than by title,
  and background sibling-window keys are refused with a usable route instead of
  a silent miss.
- Sirius never foregrounds the target app or moves your mouse to dispatch an
  action. Pointer delivery escalates only on evidence, and a re-dispatch
  requires pixel proof rather than an unchanged accessibility tree.
- A carried-over reference resolves instead of blocking, a presented sheet is
  resolved in one recovery call, and a provably ineffective click escalates
  inside the same call instead of ending the turn.
- One unconfirmed click no longer poisons every later click in the session, and
  a human approval wait no longer consumes the action-set budget.
- Declared postconditions are verified as pre/post transitions on
  `computer_use_press`, `type`, `paste`, `click_point`, and `drag`. Where the
  host does not evaluate a declaration — an element-resolved click — the
  declaration is refused with guidance instead of being accepted and ignored.

## Transcript, replies, and media

- Assistant replies render as a compact native resource quote, and a file the
  agent authored mid-turn appears in the live transcript at the moment the turn
  finishes rather than after a session switch.
- Audio and video attachments persist as tool-accessible media files with their
  identity intact, and provider projection routes each payload by the selected
  model's actual capability.
- Persisted history pages as you scroll into it without losing your reader
  position, and `read_file` is the single reader for attachment content.

## Browser challenges

- A CAPTCHA is detected and surfaced with fresh snapshot and screenshot
  evidence so an authorized model can interact with the visible challenge using
  the browser's normal controls. Automatic Turnstile and checkbox handling
  remains bounded and self-terminating.
- Paywall, login, payment, and subscription gates keep their existing human
  takeover handling. The solver-dependency, bypass-mirror, and
  identity-spoofing denylist guards are unchanged.
- A blocked browser transaction stays repairable and honest, exact-name targets
  resolve against suffixed accessible names, and interception geometry is
  anchored to the primary display.

## Providers and engine

- Updated Codex model discovery for GPT‑6.1 Sol, and public OpenAI Responses routing for its tool calls. Provider discovery and CLI dispatch adapters are included in the matching core runtime.
- Codex CLI readiness and dispatch now select the same default executable as Settings, preventing an older user-local CLI from handling requests after a system CLI update. Explicit binary overrides stay authoritative.

- Context capacity is discovered and cached per endpoint and model, so budgets
  follow what the endpoint actually serves instead of a stale constant.
- DeepSeek thinking-mode tool choice no longer produces a 400, Codex and
  compatible provider API contracts are aligned, and a provider failure is no
  longer reported as broken Goal metering.
- Tool error backoff reads the failure cause; context compression keeps recap
  timing, tool results, and evidence intact.
- CLI sub-agent runs are durable: conversations and results survive restarts, a
  queued or interrupted run is terminalized honestly, and an independent child
  whose parent consumer is gone is committed as lost rather than left running.
- Messages progress is coalesced without typing delays, and `sirius chat`
  starts for OAuth-configured providers.

## Settings and help

- The curated user guide ships in Settings and as the packaged Help Book, with
  ten pages covering setup, conversations, plans, goals, the transcript,
  projects and workspaces, panels, tools and skills, memory, privacy, and
  troubleshooting.

## Runtime

- Updates to the published SwiftPython Preview 1.1 runtime
  (`0.7.0-preview.1.1`) with matched worker and framework artifacts.
- Updates the Messages integration to the shipped SiriusMsg 0.2.0 build 17.

Requires macOS 26 or later on Apple silicon.

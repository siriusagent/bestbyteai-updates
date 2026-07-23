<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.003

**Alpha channel release.** Sirius's core product surfaces and signed update
path are stable enough for regular use. The alpha label remains a pre-1.0
release channel — updates may still refine behavior and compatibility — but
this is a user release, not an installation or packaging test.

This release makes Computer Use far less chatty and far more truthful after
each direct action — including interrupted multi-step work — migrates CLI
Agents from the retired Gemini CLI to Google's Antigravity CLI, keeps sub-agent
work visually attached to the turn that dispatched it, and stops long-lived
ChatGPT channel sessions from dying on an expired OAuth token.

## Computer Use that tells you what actually changed

- **A successful click now returns the post-action state it already observed.**
  `computer_use_click_element` and `computer_use_click_point` attach a fresh
  `snapshot_id`, the relevant elements, and a bounded `post_action_diff`
  instead of discarding the verification capture. Scripted workflows often
  continue without a separate `computer_use_observe`. Honest verification is
  unchanged: verified, unconfirmed, and not-applicable stay distinct, and an
  AX-invisible canvas click still recommends a screenshot rather than being
  silently upgraded. (BUG-365)
- **Every mutation now ends at one explicit post-action boundary.** Keyboard,
  pointer, scroll, drag, named, menu, lifecycle, and bounded transaction
  actions return one settled post state or say explicitly that the post state
  is unavailable. Interrupted typing, dragging, or edit-and-submit work
  returns the partial state already created on screen without replaying the
  action or pressing Submit; deadline exits remain non-retryable. (BUG-366)
- **Verification follows application meaning, not accessibility-tree churn.**
  Ref renumbering, focus hops, geometry, and ordering stay visible in the raw
  audit diff but cannot prove an action succeeded or later upgrade an
  inconclusive result. When the tree is large, results prefer newly relevant
  actionable refs plus raw and semantic diffs against the pre-action baseline
  instead of unchanged ribbon or grid rows that happened to land in a sample.
  (BUG-365, BUG-366)
- **Post-action captures stay on the exact window that received input.** A
  stable macOS window id is re-resolved after dispatch, including across title
  changes and overlapping same-size windows. Ambiguous or disappeared targets
  fail closed instead of borrowing a sibling window's real state change, and
  menu commands return the newly selected current surface rather than the old
  utility window. (BUG-366)
- **Stale element refs fail closed before input.** Role, label, stable AX
  identity, enabled/editable state, actions, and frame are compared before
  focus or click; a mismatch returns a concrete `stale_ref` instead of
  typing or clicking the wrong control.
- **Safe follow-up actions can consume fresh refs without weakening replay
  protection.** Sirius emits lineage only when the acted control can be
  uniquely relocated in its own post snapshot. Same-target replays, duplicate
  controls, and refs from unrelated snapshots remain blocked. (BUG-366)
- **Ordinary clicks stay ordinary clicks.** Primary click uses only
  `AXPress` / `AXOpen` / `AXConfirm`, or one verified exact-bounds left
  click for a stable frontmost control. Opening a context menu
  (`AXShowMenu`) is never substituted for a normal click.
- **Activating an app reports the window that actually came forward.**
  `computer_use_activate_app` waits for asynchronous macOS activation to
  settle, prefers the current frontmost / AX-focused window, and no longer
  presents a stale sibling (or a false `activation_failed`) when the
  activation already succeeded. (BUG-364)

## CLI Agents: Antigravity replaces Gemini CLI

- **Settings → Agent → CLI Agents now offers Google's official Antigravity
  CLI.** Install uses Google's installer, resolves the canonical
  `~/.local/bin/agy`, launches browser sign-in, exposes plan/edit sandbox
  mapping, and updates through `agy update`. Existing Gemini CLI entries
  migrate cleanly, and the default timeout is 600 seconds for longer
  Antigravity runs.

## Transcript and channel polish

- **Live sub-agent dispatches keep their parent's provider avatar and stay
  on the dispatching turn.** A fresh session no longer brands early rows as
  OpenAI while Settings is still loading, a missing provider id no longer
  renders as Ollama, and a slow Codex or CLI dispatch no longer detaches
  into its own assistant row when the parent turn moves on. Historical
  replay shares the same one-block-per-dispatch rules. (BUG-363)
- **ChatGPT OAuth no longer expires underneath long-lived channel workers.**
  Telegram and every other generic channel refresh the bearer before each
  request, so they stay aligned with newer SiriusMsg and foreground turns.
  Channel replies now show a redacted provider reason and distinguish 401
  sign-in failures from 403 model or account denial. (BUG-362)

## Notes

- **Sparkle build version** is `128` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `127` or earlier will offer
  this release.
- The signed core-runtime feed is refreshed as `0.1.1-alpha.003` so the app,
  appcast, and Python runtime component remain release-synchronized.

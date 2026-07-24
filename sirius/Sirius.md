<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.006

**Alpha channel release.** Sirius's core product surfaces and signed update
path are stable enough for regular use. The alpha label remains a pre-1.0
release channel — updates may still refine behavior and compatibility — but
this is a user release, not an installation or packaging test.

This is a second same-day fix release for the Computer Use regressions from
v0.1.1-alpha.004, covering both halves of the stack: the Swift host's click
transport selection (which silently no-oped every ref click in a frontmost
window on AX-only views) and the Python engine's replay-safety guard (three
more rounds of over-blocking found by live re-tests).

## Fixed

- **Frontmost ref clicks silently no-oped on AX-only views (BUG-370).** The
  alpha.004 transport selection routed every labeled command control in an
  already-frontmost window through a one-shot HID coordinate click without
  attempting AXPress. Views that ignore synthetic CGEvents but honor AXPress
  — Chess's 3D board is one — lost every click exactly when their window was
  frontmost, while backgrounded windows kept working. The HID direct
  transport is now reserved for refs that advertise no primary AX action;
  AXPress-capable controls always dispatch AXPress, verified against a live
  Chess board where AXPress completes moves every time and HID/postToPid
  clicks never land.

- **Computer Use replay safety still blocked distinct targets after
  alpha.005's fix.** A click sourced from a fresh `computer_use_activate_app`
  snapshot (rather than `computer_use_observe`) stayed blocked, because the
  escape hatch only trusted observe results even though every computer-use
  mutation attaches the same settled snapshot shape. A coordinate
  `computer_use_click_point` following a ref-identified unconfirmed click had
  no escape hatch at all. Both are fixed: the fresh-ref scan no longer cares
  which tool produced the snapshot, and a ref-identified prior target is
  re-identified by role/label into a fresh box so a coordinate follow-up can
  be checked against where that control actually is now. Regression tests
  reproduce both gaps from the live session that exposed them, including a
  same-target coordinate replay that must still fail closed.
- **Replay safety starved when element projection returned zero lines.**
  When a click's post-action diff is unchanged, the host's `delta_relevant`
  projection returns no element lines at all, leaving the guard with no
  fresh element evidence anywhere in history. A ref click grounded in a
  snapshot minted strictly after the unconfirmed mutation is now allowed
  when no semantic identity is recoverable — acting on returned post-action
  state is exactly what the block message prescribes, and the host still
  validates the snapshot/ref pairing at dispatch. Coordinate clicks can now
  be checked against the prior control's bounds from a pre-mutation
  observation when the window frame is unchanged. Same-target replays —
  same ref from the unconfirmed click's own snapshot, or a point inside the
  prior control's box — still fail closed, and a fresh snapshot whose
  keyboard focus never left the prior text field still blocks typing.
- **Label-identified actions after an unconfirmed coordinate click no longer
  block on distinct controls.** A `computer_use_transaction` press targeting
  a control by (role, label) carries no coordinate bounds, so it could not
  be compared against a prior unconfirmed point click and failed closed even
  when the point was nowhere near that control. The requested target's box
  is now re-identified from history symmetrically with the prior-target
  case; a request whose box contains the unconfirmed point still fails
  closed. Verified against a live multi-move Chess session in which the
  guard also correctly blocked a genuine same-target coordinate replay.
- **A successful Computer Use recovery no longer bans the tool family
  (BUG-371).** After a no-progress replan, the engine restarted its stall
  detector with a threshold so tight that the very first result — including
  the verified, state-changing bounded transaction the replan itself asked
  for — counted as "no progress", exhausted recovery, and hid every
  computer-use tool for the rest of the turn. The tightened phase now
  compares results against the fingerprint the work actually stalled on,
  a verified interaction with a new fingerprint heals the phase, and the
  full native toolset is restored so long-running desktop tasks can
  continue. Genuinely unchanged or blocked work still exhausts recovery
  exactly as before. Additionally, a legitimate two-step interaction —
  select a source control (honestly `unconfirmed`, since selection paints
  no AX diff), refresh evidence, then act on a distinct destination — no
  longer counts toward no-progress before the destination is attempted;
  observing forever or attempting a second fruitless action still trips
  the classifier.
- **Recovery honors explicit tool-family constraints (BUG-371).** When the
  request says "Use only the Computer Use tools", every other action tool
  (browser, vision, Music, shell, …) is denied for the turn and recovery
  guidance never proposes another family as the fallback — it prefers the
  bounded same-family transaction/scroll or stops with the concrete
  verified blocker.
- **A "non-\<family\>" adjective no longer bans the family it exempts
  (BUG-372).** Prompts ending "…or any other non-Computer-Use action tool"
  used to prohibit every Computer Use tool, colliding with the exclusivity
  constraint above and leaving no callable action tools. The negation
  parser now discounts "non-"-prefixed mentions, and a positive
  exclusivity constraint takes precedence over any same-family lexical
  negation match ("anything other than Computer Use tools"). Standalone
  real negations and explicitly named prohibitions still apply.
- **Distinct drag paths and post-raise point clicks no longer false-block
  (BUG-373).** Drag identity now compares the full `(x1,y1)->(x2,y2)` path
  instead of collapsing to bare pid/window/operation, so a different
  endpoint after an unconfirmed drag is allowed while an exact-path replay
  still fails closed. An unconfirmed window-level `raise` no longer leaves
  a whole-window bounding box that blocked every later coordinate click in
  that window.

## Notes

- **Sparkle build version** is `131` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `130` or earlier will offer
  this release.
- This release changes the Swift host (`ComputerUseRunner` transport
  selection) and Python engine code (`sirius_agent/engine/tool_cycles.py`);
  the signed core-runtime feed is refreshed as `0.1.1-alpha.006` to carry
  the engine fix.

<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.2-alpha.005

Alpha.005 is a focused macOS host patch for six verified interaction and
state-boundary defects in Alpha.004.

## Transcript controls no longer leave a blue focus rectangle

- Clicking ordinary activity, search, tool, and reasoning disclosure rows no
  longer transfers keyboard focus into generic transcript controls.
- Keyboard focus and Return/Space activation remain available for sub-agent
  inspector controls that intentionally require them.
- The repaired policy is covered by mounted AppKit pixel and activation tests.

## Conversation history cannot cross session boundaries

- Clearing a slot for a fresh conversation now invalidates any older-history
  request still in flight for the previous session.
- A late page can no longer prepend old rows into the new chat after the first
  message is sent.

## The Chats sidebar reports real load state

- The bridge's initial empty publisher value no longer masquerades as a
  completed database query.
- Chats show **Loading chats…** until SQLite answers, **No chats** only after a
  successful empty result, and an accessible Retry action after failure.

## Canceled turn controls stay canceled

- A Stop, Steer, Goal, or sub-agent control canceled while waiting behind
  another control is removed from the submission queue.
- Cancellation racing gate ownership releases that ownership without sending
  the stale mutation or wedging later controls.

## Provider changes are atomic and honestly reported

- Active-provider backend changes resolve a valid model before publishing or
  saving the new selection. Sirius no longer hot-swaps an intermediate empty
  model that temporarily puts channels into fail-closed mode.
- Superseded catalogue results cannot overwrite a newer picker choice.
- The green success chip now appears only after both the configuration write
  and live provider fan-out succeed; failures use the existing error surface
  instead of a timer-generated success message.

## Notes

- Sparkle build version is `161` (`CFBundleVersion`). Apps on build `160` or
  earlier will be offered this release.
- The signed ABI-1 core runtime remains engine version `2026.08.30.4`; this
  release changes only the macOS host and reuses the already verified runtime
  feed.

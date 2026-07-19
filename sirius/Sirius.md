<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.125

**Strict pre-release unstable build.** This alpha is for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This release makes native computer-use and in-app browser automation land
single, verified, bounded actions instead of loose click/type sequences,
closes a gap where Stop during a silent model response respawned a healthy
worker, and adds a durable turn ledger so a crashed worker can no longer
silently duplicate or half-replay a turn.

## More reliable native app control (computer use)

- **`computer_use_transaction` replaces ad-hoc click/type sequences with one
  finite, deadline-bounded recipe.** `find_and_act_and_settle` resolves one
  exact control and presses or sets it once; `edit_and_submit` resolves the
  field and its submit control together, edits, verifies the exact value,
  then submits once; `wait_for_condition` polls without mutating anything.
  Every recipe returns verified post-action evidence in the same result, so
  the agent stops thrashing through repeated observe/click loops on stale or
  ambiguous targets.
- **`computer_use_edit_text` replaces a whole field or document and reads it
  back for exact equality — without submitting or moving focus.** This
  removes a class of mistakes where correcting text in a form or document
  accidentally triggered Return/submit before the value was right.

## More reliable in-app browser automation

- **`browser_use_transaction` brings the same bounded recipes to the
  browser panel**, returning a verified post-action snapshot and semantic
  diff in one result instead of a separate observe-then-act round trip.
- **Ambiguous mutations can no longer be silently retried.** If a mutating
  transaction (a submit, a click that changes state) comes back ambiguous,
  Sirius blocks another mutating transaction against that same target for
  the rest of the current page/navigation — closing off double-submits and
  duplicate clicks after a timeout where the first attempt may have already
  landed. Navigating away and back starts a fresh window; read-only waits
  are never blocked.

## Turn durability and Stop reliability

- **Stop now works during a silent model response instead of respawning a
  healthy worker.** Cancelling a turn while the provider has gone quiet
  aborts the in-flight request directly, marks the attempt cancelled, and
  returns the session to idle — it no longer gets misclassified as a wedged
  stream and replaced with a fresh worker mid-conversation. (BUG-356)
- **A durable turn-execution ledger protects against duplicated or
  half-replayed turns after a worker crash.** Sirius now records message
  commits and tool-mutation boundaries as they happen, so recovery after an
  unexpected worker loss can only safely resume a turn that provably made no
  side effects and delivered no partial output — otherwise it fails closed
  with an explicit recovery error instead of guessing.

## Notes

- **Sparkle build version** is `125` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `124` or earlier will offer
  this release.
- The signed core-runtime feed is refreshed as `0.1.0-alpha.125` so the app,
  appcast, and Python runtime component remain release-synchronized.

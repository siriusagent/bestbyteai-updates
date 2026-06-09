<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.35

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixes a mid-conversation failure where a turn could die with
  "Worker N is not responding" while a long terminal command was running.
  Under critical system resource pressure (memory, thermal, or saturated
  host CPU), the worker pool's idle-shed recovery could shut down a worker
  that was actively streaming a turn with an in-flight terminal command,
  orphan the running command, fail the visible session, and immediately
  respawn the worker it had just killed. The pool runtime now never sheds
  a worker with in-flight work, even under critical-pressure force sheds
  (SwiftPython 0.5.14).
- Adds log evidence for worker shedding and host memory-pressure
  transitions so any future pool recovery has its trigger on the record in
  the app log instead of a transient status pill only.
- Hardens session startup so configuration loading no longer depends on
  app-boot ordering for the embedded Python import path.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

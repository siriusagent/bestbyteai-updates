<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.123

**Strict pre-release unstable build.** This alpha is for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This release lets several conversations stay live in one window, makes web
research faster and fail-closed around the exact captured resource, and
hardens session startup, background completion, and app shutdown after the
multi-session release gate exposed their remaining concurrency edges.

## Multiple live conversations

- **Switching chats no longer stops work in the conversation you leave.** Each
  active conversation has its own controller, transcript, event pump, and
  worker-backed slot, so turns, Goals, watched commands, and background wakes
  can continue while another chat is focused.
- **The sidebar is now the live-session switcher.** Its leading status shows
  local work, channel work, approval needed, worker-capacity wait, or idle
  history. Reopening an active Goal reconciles queued events and re-arms its
  continuation instead of leaving chrome-only activity behind.
- **Capacity grows safely.** Sirius consumes SwiftPython 0.5.15 and can add
  process workers up to a conservative ceiling. A conversation that cannot be
  admitted immediately opens read-only, explains that it is waiting, and
  connects automatically when a worker becomes available.
- **Focus changes cannot retarget in-flight actions.** Send, research, steer,
  plan, clarification, Goal commands, dictation drafts, deletion, channel
  refresh, and window teardown remain bound to the conversation that started
  them.

## Faster, trustworthy research

- **Host-backed search and reads prove what was captured.** Successful results
  expose their validated request ID, requested and final URL, navigation proof,
  and integrity outcome. A stale or mismatched Research capture fails closed as
  a body-free resource mismatch.
- **Independent reads can overlap without taking over user tabs.** Sirius uses
  three isolated Research lanes for contiguous read-only work, preserves
  result order, and invalidates leases and waiters on cancellation or shutdown.
- **Documents keep stronger evidence.** Digital PDFs use a conservative native
  text fast path with page maps, while downloaded documents record their hash
  and download count. Read-only research failures no longer force an
  unnecessary model turn.

## Session and shutdown reliability

- **Cold startup no longer loses a worker to overlapping control calls.**
  Lifecycle, Settings, and callback operations share a FIFO gate per worker
  while unrelated workers remain concurrent; cold session construction gets a
  bounded 120-second budget.
- **Background completions clear their sidebar state.** Acked terminal events
  mark their task surfaced, return post-ack task and watch counts, treat the
  terminal `.acked` wake state as quiescent, and exclude the wake turn's own
  claimed event from fresh-work detection. A lifecycle reconciler repairs any
  future missed projection input.
- **Cancelled foreground commands cannot become phantom background tasks.**
  Stream teardown aborts the active command, suppresses auto-background
  adoption, and reconciles incomplete recovered records from their footer or
  marks them lost.
- **Command-Q preempts host-owned terminal work before worker close RPCs.**
  Sirius stops active agent process groups, resolves their terminal callbacks,
  cancels streams, and then performs reflection and worker teardown. Tracked
  sessions also receive a durable reflection fallback, including sessions whose
  cached handle changed during a host-bridge rebind.

## Safety hardening

- **DiffTree stays detached from the home directory.** Startup and explicit
  scan/watch requests reject home and symlinks resolving to home.
- **The throwaway launcher fails closed around shared app identity.** It will
  not coexist with another Sirius process or alias the real `~/.sirius`, and it
  reports only the process created by the current launch.

## Notes

- **Sparkle build version** is `123` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `122` or earlier will offer
  this release.
- The signed core-runtime feed is refreshed as `0.1.0-alpha.123` so the app,
  appcast, and Python runtime component remain release-synchronized.

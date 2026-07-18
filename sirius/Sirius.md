<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.124

**Strict pre-release unstable build.** This alpha is for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This release keeps several conversations visibly live in one window, makes web
research faster and fail-closed around the exact captured resource, and
hardens session startup, background completion, and app shutdown around the
remaining concurrency edges exposed by the multi-session release gate.

## Multiple live conversations

- **Switching chats no longer stops work in the conversation you leave.** Each
  active conversation has its own controller, transcript, event pump, and
  worker-backed slot, so turns, Goals, watched commands, and background wakes
  can continue while another chat is focused.
- **Every live conversation keeps its place in the sidebar.** Fresh sessions
  retain their own `New chat` row while work continues elsewhere, and each
  persisted conversation replaces only its matching placeholder. The first
  completed exchange can title the row without waiting for another turn.
- **Sidebar status follows the conversation lifecycle.** Active generation uses
  a compact spinner, successful background completion stays blue until the row
  is focused, failures or approval needs are red, worker-capacity wait is
  hollow orange, and dormant history remains grey. Reduce Motion uses a static
  ring, and every state has an explicit accessibility label.
- **Capacity grows safely.** Sirius consumes SwiftPython 0.5.15 and can add
  process workers up to a conservative ceiling. A conversation that cannot be
  admitted immediately opens read-only, explains that it is waiting, and
  connects automatically when a worker becomes available.
- **Focus changes cannot retarget in-flight actions or host automation.** Send,
  research, steer, plan, clarification, Goal commands, dictation drafts,
  deletion, channel refresh, and window teardown remain bound to the
  conversation that started them. Terminal and browser routes follow their
  owning session without rebuilding unrelated live handles.

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
- **Background completions leave accurate sidebar state.** Acked terminal
  events mark their task surfaced, return post-ack task and watch counts, treat
  the terminal `.acked` wake state as quiescent, and exclude the wake turn's own
  claimed event from fresh-work detection. A lifecycle reconciler repairs any
  future missed projection input, while an unseen completed turn remains easy
  to find until it is focused.
- **Session-aware host bridges stay stable as chats change.** Adding or focusing
  another live conversation updates terminal and browser coordinator routing
  in place instead of invalidating unrelated worker bindings, preserving
  background completion, first-turn titles, and browser automation continuity.
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

- **Sparkle build version** is `124` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `123` or earlier will offer
  this release.
- The signed core-runtime feed is refreshed as `0.1.0-alpha.124` so the app,
  appcast, and Python runtime component remain release-synchronized.

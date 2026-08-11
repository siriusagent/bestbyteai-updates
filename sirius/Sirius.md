<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.020

Alpha.020 replaces Auto's parallel permission policy with the contract it was
supposed to have: Permissive behavior, plus model review only where Permissive
would have asked a human. The reviewer now sees the task Sirius is actually
executing and returns a reason that is preserved for the agent and audit.

## Fixed

- **Conservative shell projection is evidence, not a verdict (BUG-408).** The
  exact executable syntax can resolve same-command literal bindings and quoted
  payloads; genuinely dynamic targets remain blocked. The v5 overlay retains
  the semantic correction proven by the earlier v4 prompt-only A/B.
- **Auto literally inherits Permissive (BUG-409).** A call Permissive silently
  admits follows the same path in Auto and makes zero reviewer calls. This
  removes the second, stricter policy track that was denying ordinary agentic
  work.
- **Auto substitutes review only at the human-approval boundary.** One
  structured model review handles reviewable cases where Permissive would
  prompt. Hard denies remain terminal. Explicitly nondelegable credential
  disclosure, ungranted wallet spend, MCP `ask`, and unsupported
  credential/economic submissions still require a human and never reach the
  reviewer.
- **The reviewer sees authority and context as different things.** Trusted
  human messages establish authority. Goal/Plan state, model-authored action
  intent, recent tool evidence, the exact candidate/direct parent, and runtime
  facts support interpretation without silently becoming authority or a
  precomputed verdict.
- **Review decisions explain themselves.** The structured result carries an
  authority basis, intent alignment, effect summary, bounded explanation, risk
  tags, and confidence. The acting model and redacted authority audit retain
  those reasons.
- **Runtime locus is evidence, not the answer.** Literal bindings, quoted
  heredocs, and explicit repository-bootstrap authority can establish a bounded
  target even when a coarse projection reports `unresolved`; active variable,
  command, process, and arithmetic substitution remain unresolved and block.

## Verification and certification status

- The exact two persisted calls from Sirius session
  `4615a8c9-b74e-4c54-91b5-fdfbe192e169` now route through
  `permissive_baseline` and allow with zero reviewer calls.
- Direct GPT-5.6 Luna v5 replays of those byte-for-byte candidates also allowed
  both and cited the operative human authority. An earlier v4 prompt-only A/B
  established the shell-projection correction; the first combined overlay
  prompt iteration still reproduced both blocks until v5 integrated that rule.
  Both experiments and the failed intermediate assumption remain recorded.
- Four live provider-backed controls blocked an unbound target variable,
  command-substitution targeting, recursive deletion outside the assigned
  workspace, and a remote push contradicting the latest human steer.
- Focused permission/authority coverage passed 614 tests. The broader affected
  suite passed 1,561 tests with 11 skips. Existing child-process hardware-probe
  crash diagnostics appeared in that broader run, but pytest recovered and
  exited successfully; the clean focused slice did not emit them.
- The combined native host suite passed 3,248 tests with 18 skips. One
  post-activation evidence fixture initially exhausted its 100 ms wall-clock
  budget on the loaded release machine; its fixture-only budget was corrected,
  the case passed three consecutive runs, and the full suite then passed.
- This is production-trace regression evidence, not a replacement statistical
  certificate for the invalidated alpha.017/alpha.018 synthetic gates.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 145 with the matching signed core-runtime feed.

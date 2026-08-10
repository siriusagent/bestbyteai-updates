<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.018

Alpha.017 described automatic permissions, but its shipped native route could
still send harmless readers through a slow classifier and let one stuck request
turn later actions into timeout denials. Alpha.018 fixes and live-certifies the
actual SwiftUI product path.

## Fixed

- **Read-only tools are automatic now.** Tools declared never-mutating, such as
  skill listing, file reads, and credential availability checks, pass through a
  deterministic policy after hooks and hard checks. They do not spend a model
  call or open a permission sheet.
- **Consequential actions use the configured background provider.** The native
  session forwards mutation metadata across foreground, isolated, and DAG tool
  dispatch. OpenAI classification uses Sirius's API key and public endpoint;
  the user's foreground ChatGPT OAuth session and other background consumers
  are unchanged.
- **GPT-5.6 permission verdicts use no reasoning.** The narrow classifier call
  is fast and non-blocking while ambiguous cases can still use the policy's
  second stage.
- **A stuck classifier request cannot poison the queue.** Timed-out workers are
  retired with bounded rotation, so later actions are evaluated independently
  instead of failing in long timeout cascades.
- **Authority history tells the truth.** Native Settings and durable audit rows
  distinguish deterministic read policy, model allow/block decisions, and
  fail-closed boundaries without recording secrets or hidden reasoning.

## Certified release gate

- Frozen GPT-5.6 Luna holdout: 13,219 cases.
- Benign false positives: 20 / 10,000 (0.20%; one-sided 95% Wilson upper
  0.288171%).
- Destructive misses: 0 / 2,000; overeager-action misses: 0 / 200.
- Eligible-safe prompts and hard-policy, human-authority, injection,
  delegation, and cross-surface escapes: zero.
- Stage-one p95: 1,269 ms; stage-two total p95: 3,039 ms.
- Notarized native A1-A7 matrix: deterministic readers passed; harmless shell
  read, bounded write, and exact task-owned recursive cleanup passed; the
  privilege-boundary probe was blocked before execution.

The corpus and Anthropic's private Auto Mode corpora differ, so the numeric
comparison remains qualified rather than an apples-to-apples replication.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 143 with the matching signed core-runtime feed.

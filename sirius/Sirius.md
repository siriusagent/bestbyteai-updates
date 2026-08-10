<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.017

This alpha makes **Auto** a real automatic permission mode. Sirius now uses
the configured background provider to classify consequential actions while
preserving deterministic hard-deny, human-only-authority, and runtime-ownership
boundaries.

## Changed

- **Safe, explicitly authorized work can proceed without routine approval
  prompts.** The classifier receives a narrow projection of human intent and
  the proposed action, not hidden reasoning or untrusted tool-result text. A
  fast first stage handles clear cases; a reasoned second stage handles
  ambiguity.
- **Denied actions fail closed and the agent keeps working.** Sirius records the
  denial and returns it to the active agent so it can explain or replan instead
  of turning every uncertain action into a blocking permission sheet.
- **Owned scratch cleanup is deterministic.** Sirius-created temporary resources
  carry session-scoped ownership proof, so their bounded recursive cleanup does
  not need model or human review. Arbitrary project or `/tmp` paths are never
  inferred to be owned.
- **One permission gate covers every execution surface.** Foreground calls, DAG
  children, skills, sub-agents, channels, resumed sessions, and background-
  provider hot swaps share the same semantics and redacted audit trail.
- **Settings shows the truth.** Native permission status and authority history
  identify deterministic, ownership, model, human, and fail-closed outcomes
  without exposing secrets or hidden reasoning.

## Certified release gate

For the recorded `gpt-5.4-mini` model and policy inputs, Sirius **exceeds the
published Anthropic Auto Mode numeric bar on Sirius's frozen corpus**:

- 0.03% benign false positives across 10,000 eligible safe actions (Anthropic
  reports 0.4% on its private corpus).
- Zero misses across 200 curated overeager actions and 2,000 synthetic
  destruction/exfiltration actions (Anthropic reports 17% and 5.7%,
  respectively, on its private corpora).
- Zero eligible-safe prompts and zero hard-policy, human-authority, injection,
  delegation, execution-surface, or trigger-session escapes.
- Stage-one p95 of 812ms and stage-two total p95 of 2.1s under the frozen
  16-lane release protocol.

The private corpora differ, so this is a qualified numeric comparison, not an
apples-to-apples replication. See the checked-in
[literal Sirius certification record](https://github.com/mikhutchinson/sirius-agent/blob/master/.plan/Sirius%20Automatic%20Permission%20Classification%20Plan/RESULTS-2026-08-10.md)
and Anthropic's published
[Auto Mode report](https://www.anthropic.com/engineering/claude-code-auto-mode).

## Fixed

- **Background command watches now reject impossible output contracts
  (BUG-405).** Sirius will not arm a watcher after the command redirects both
  stdout and stderr away from its transcript; the error explains how to retain
  observable output with `tee`.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 142 with the matching signed core-runtime feed.

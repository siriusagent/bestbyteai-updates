<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.024

Alpha.024 is a focused hotfix for local Ollama models whose chat templates
require system messages to appear before all conversation content.

## Ollama hotfix

- **Qwen3.8 and other strict templates now accept Sirius agent turns.** The
  Ollama adapter preserves Sirius's complete leading structured system prefix
  and translates only later current-turn recovery, routing, tool-availability,
  and nudge hints into the user lane at their original temporal position.
- **Sirius behavior outside Ollama is unchanged.** Provider-neutral prompts,
  tool schemas, permissions, session lifecycle, and every other provider keep
  their existing paths.
- **Ollama failures are actionable.** JSON error details from the local daemon
  now appear in Sirius diagnostics instead of collapsing to a generic HTTP 500
  traceback.

## Verification

- The complete non-slow Python gate passed 7,812 tests with 17 skips and 13
  deselections.
- The focused Ollama provider, streaming, override, cloud, and probe gate
  passed 84 tests with one opt-in live-network test skipped.
- Ruff, exact wiki drift, and diff checks passed.

## Distribution

- macOS 26 (Tahoe) or later.
- Developer ID signed and Apple notarized.
- Sparkle build 149 with the matching signed core-runtime feed.

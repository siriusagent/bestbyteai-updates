<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.87

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- **Mind graph search is now typed and ranked.** Graph queries can use
  structured filters such as kind, tool, project, file, session, skill, section,
  pinned state, and time windows, with ranked result rows and suggestions in
  the right rail.
- **Mind graph detail loading is narrower and less stale.** Selected-node
  detail hydrates only the relevant node context, rejects slow responses for
  superseded selections, and suppresses stale project edges for detached
  sessions.
- **DiffTree fast-path navigation now matches Git visibility.** The first
  navigator paint resolves the repository root and uses `git ls-files`, so
  tracked dotfiles appear immediately while ignored files stay hidden before
  Git chrome promotion finishes.
- **The distributable build defaults now target alpha.87 / build 87.**

## Distribution

- Published as monotonic Sparkle build 87.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

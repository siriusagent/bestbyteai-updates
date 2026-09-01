<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.032

We owe you an apology. Sirius 0.1.2 was unacceptably unstable, and shipping
builds 157 through 161 damaged your trust. Those releases remain withdrawn.
Alpha.032 is a deliberately narrow recovery patch on the stable 0.1.1 line,
with a monotonic build number so it reaches both rollback users and anyone who
still has a withdrawn 0.1.2 build installed.

Features quarantined from 0.1.2 have not been merged back wholesale. They will
be restored only after the same extensive signed-app, clean-install,
long-session, cross-session, cancellation, provider, browser, runtime, and
public-update testing applied to this patch.

## MCP works end to end again

- Sirius now pins MCP 2.1.1 exactly and uses its current streamable-HTTP,
  result-decoding, server, and OAuth contracts.
- OAuth completes protected-resource discovery, authorization-server metadata,
  dynamic client registration, PKCE authorization, callback validation, token
  exchange, secure token persistence, and authenticated tool calls.
- Both stdio and OAuth MCP tools were loaded and called from real workers in a
  freshly signed isolated Sirius app.

## The embedded Python runtime is self-contained

- Sirius now ships `swiftpython-commercial` `0.6.0-duplex.8.3` at exact
  revision `84c0707ba3eb39ae3a8b234614856900314f5e59`.
- Workers load Python only from
  `Sirius.app/Contents/Frameworks/Python.framework`, including when launched
  with a hostile `PYTHONHOME` and restricted `PATH`.
- A signed worker completed `asyncio.current_task()` and
  `asyncio.wait_for()`; Python created no new bytecode in the framework and
  strict code-sign verification still passed after launch.
- Optional components now install through a signed app-owned helper linked to
  that same framework. The signed core runtime supplies pip; Sirius no longer
  discovers or falls back to Homebrew, python.org, PATH, or another host Python.

## Agent and tool reliability

- A valid planning event no longer makes a successful turn fail as malformed.
- Google pages that hide result destinations behind opaque `/goto` links now
  recover the visible public URL instead of returning an empty result set.
- Beautiful Soup and Markdownify are included in the signed core runtime, so
  native web reads and searches do not depend on an optional browser component.
- Qualified instructions such as “do not call tools separately outside
  `execute_dag`” no longer prohibit the DAG route the user explicitly asked
  Sirius to use.

## Verification

- Python: 8,000 passed, 40 skipped.
- Swift: 3,750 XCTest cases passed, 23 skipped, plus 13 Swift Testing cases.
- Fresh signed-app sessions covered plan, goal, browser, shell, file
  reads/writes, web tools, DAGs, MCP, memory, session search, consolidation,
  reflections, and worker replacement.
- The signed app and DMG, Apple notarization and stapling, Sparkle and core
  runtime signatures, update-feed publication, and hosted-byte identity are
  required before this release is considered shipped.

Thank you for sticking with Sirius while we corrected this. We are sorry the
0.1.2 releases reached you in that state.

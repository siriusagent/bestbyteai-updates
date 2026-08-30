<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.2-alpha.001

Alpha.001 opens the 0.1.2 line. It ships callable sub-agent runtime v2 with a
contextual inspector, signed ABI-scoped engine updates, native website Keychain
fill and opt-in Site Tools, a forensic Share Feedback workflow, and Goal /
browser reliability work.

## Inspect one sub-agent run without leaving the conversation

- Opening a quiet retained sub-agent row replaces the right panel with a
  **Subagents** workspace for that exact run: conversation owner, runtime
  session, parent call, and presentation key. A missing lookup stays
  unavailable instead of guessing by agent name or run ID.
- The roster is read-only. Active rows show title, state, and elapsed time;
  done rows show title and completion-relative time. Both sections are
  newest-first, with **Show more** instead of an unbounded log.
- Run detail is one child transcript using the same inline tool drawers,
  search/browser routing, Dynamic UI, vision, grouping, and progress as the
  main conversation. Exact worker-lifetime inspect and one-shot Stop stay
  independently receipt-bound. **Close** restores the panel module that was
  open before inspection.
- Parent sessions can now dispatch a heterogeneous frozen catalog across local
  children and an exact Sirius CLI definition through the closed `agent-v2`
  subprocess protocol. There is no raw-output or compatibility-replay
  fallback.

## Website passwords and Site Tools stay in the native browser

- `browser_use_fill_login` fills from macOS Keychain against the exact
  observed tab, snapshot, and field ref. The agent never receives account
  identity, password bytes, or page secrets; form submission remains a
  separate browser action. The same Keychain control is available from the
  focused login field.
- Imperative WebMCP Site Tools use the draft `document.modelContext`
  contract. Discovery is default-off until **Allow Site Tools** is enabled
  for that exact origin and the already-loaded page is reloaded. Every call
  still passes the normal permission gate. Receipts are five-minute and
  single-use, bound to the exact session, tab, document, and registration
  revision.

## Share Feedback is a forensic report, not a bug form

- Intake uses a native hierarchy, adaptive intent cards, one large report
  field, working evidence controls, and a pinned primary action.
- Review exposes editable executive fields, findings, citations, privacy,
  exact selectable Markdown, and destination receipts. The schema now
  carries incident impact, metrics, timeline, causal chain, numbered
  severity/confidence findings, explicit negatives, remediation, acceptance
  tests, unresolved questions, and an evidence index.
- The worker reconstructs bounded focused-session model, tool, and ledger
  evidence from `sirius.db`. The model boundary and saved findings are
  scrubbed; the full session ID remains an internal lookup key.
- Draft and privacy edits advance the report revision and replace the
  auto-saved bundle atomically. Finder reveal verifies bytes, policy,
  revision, and digest before opening.

## Goals stay on the Goal you confirmed

- Existing-Goal mutations are id-and-revision fenced. The model can amend,
  block, resume, and clear without creating a replacement Goal. Completion
  and configured verification require current evidence.
- Pause, Clear, and End carry the Goal identity that was actually confirmed.
  The End sheet scrolls only the objective, pins Cancel and End/Clear, and
  restores the control panel on cancellation or failure.
- Idle active Goals expose **Continue Goal** beside Pause. Between-turn
  actions wait for an authoritative newer snapshot or surface the worker
  error instead of acting on optimistic UI intent.
- Goal-owned background resources cannot leak into a replacement Goal.

## Browser automation is more exact

- Retry-safe target ambiguities keep a bounded, sanitized set of candidate
  refs on the same snapshot. The agent can pick one without a redundant
  observe or find; candidates drop once a newer result makes those refs
  historical.
- Dynamic DOM actions fail closed. Exact-target trusted input is serialized,
  overlay and transaction verification is stronger, and mutation provenance
  is preserved.
- Local-path and session-attachment reads are one model-facing `read_file`
  tool. Historical `read_attachment` calls still replay as a hidden alias.

## Engine updates are signed and ABI-scoped

- Components → **Sirius Engine** checks
  `https://updates.bestbyteai.com/sirius/runtime/abi-1/core-runtime.json`
  directly. The schema-2 manifest is Ed25519-signed and binds archive size,
  SHA-256, tree digest, runtime-input digest, lock digest, independent engine
  version `2026.08.30.1`, and host ABI `1`.
- A changed engine is staged. Workers switch together only after **Restart
  Sirius**. The known-good engine stays active until then.
- Already-shipped `0.1.1` apps keep using the legacy unscoped schema-1 feed.
  This release does not overwrite that feed.
- Subprocesses (CLI children, background bash, macOS automation) go through
  a host-owned, fork-safe process broker instead of ad-hoc spawns.

## Delivery and logs

- Final agent replies no longer replace ordinary phone numbers or email
  addresses with PII markers. Direct delivery still scrubs registered
  secrets, credential-shaped tokens, SSNs, and payment cards. Logs,
  transcripts, tool events, memory, and diagnostics keep full
  PII-and-secret redaction.
- Python workers prune dead or rotated Sirius logs after 14 days and enforce
  a 250 MiB directory cap. Live worker log files are never unlinked.

## Notes

- SwiftPython remains the published `swiftpython-commercial` `0.6.0-duplex.8.1`
  pin at revision `b442d26294705ff6a55bb800d370cb5b8856d1fb`. SiriusMarkdown
  remains `0.6.26` at `1a7a03b00e446eed1dc277f5e284c4515c9db292`. Both are the
  latest public tags.
- The iMessage channel client now consumes SiriusMsg `0.0.1-alpha.15` at
  `d83d67cd777aba7007e5340b1cc94f2b8b9ae50d`, including durable send-operation
  identifiers and bounded allowlisted history APIs. Sirius still does not
  own Messages access.
- Sparkle build version is `157` (`CFBundleVersion`), the primary comparison
  key for auto-update. Apps on build `156` or earlier will be offered this
  release.
- The signed core-runtime feed is the first public ABI-1 schema-2 channel,
  engine version `2026.08.30.1`, built with app version `0.1.2-alpha.001`.

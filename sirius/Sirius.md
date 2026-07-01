<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.101

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This release cleans up two quality regressions that surfaced during a
Wikipedia-extraction session: noisy `web_read` output on structured pages, and
QuickMenu toggles that flipped in the UI without reaching the engine.

## Changes

- **`web_read` stops shredding MediaWiki-style structured pages.** A new
  `_strip_structural_noise` pre-extraction pass removes unambiguous non-content
  chrome (infobox/navbox/sidebar/reflist/hatnote/ambox/metadata, citation
  superscripts, reference lists, edit-section links, `script`/`style`/`svg`/
  `iframe`, and `aria-hidden`/`hidden`/`display:none` nodes) **before**
  trafilatura and markdownify see the HTML. The class-token regex uses
  hyphen-aware lookarounds so a token like `vector-toc-available` on `<html>`
  is not matched as `toc` — the trap that deleted the whole document in the
  first cut. On non-MediaWiki pages the strip only removes universal
  never-content elements, so trafilatura's input is byte-equivalent for the
  boilerplate it already handles.
- **Citation and broken-table noise stripped from extracted Markdown.**
  `_cleanup_markdown` now drops markdown links whose anchor text is a bare
  numeric bracket (`[[4]](url)`, `[[4]]`) or a Wikipedia maintenance tag
  (`[failed verification]`, `[citation needed]`, `[dubious – discuss]`, …) while
  leaving real prose links (`[Anthropic](url)`) untouched, and
  `_drop_broken_tables` removes tables whose header row is entirely empty
  cells (the infobox/navbox shred shape). Tables with at least one real header
  are preserved.
- **Table-heavy pages fall back to the full-HTML extractor when trafilatura
  drops data rows.** When trafilatura succeeds but the markdownify fallback
  carries a ≥50 table-row advantage and ≥3× content (with a 1000-char floor),
  `_extract_page_content` prefers the fallback — recovering the 243 data rows
  of a "List of countries by GDP" page that trafilatura reduced to 4834 chars.
  The high bar keeps 40-row file-browser / nav tables (GitHub repo pages, docs
  sidebars) on trafilatura, where the fallback would drag in chrome alongside
  the rows. No Wikipedia-specific URL shortcut — the fix targets the
  extraction artifacts, not the site.
- **QuickMenu "Temporary chat" now actually skips persistence.** The toggle
  maps to `SessionConfig.persist = !temporaryChat` and is read from
  `session.quickMenu` in `restartCurrentSession` before the new chat is built,
  so a temporary chat no longer lands rows in `~/.sirius/sirius.db`. Swift-only
  change; the `persist` wire field already flowed end-to-end. Resume and
  bootstrap paths stay on `persist: true` (resume requires it; bootstrap has no
  user toggle state yet).
- **QuickMenu "Memory & profile nudges" now reaches the engine as a per-session
  suppress override.** Added optional `memory_nudge_enabled` /
  `profile_nudge_enabled` (`bool | None`) to `SessionConfigPOD`; `build_session`
  resolves each override against the `PersistentConfig` snapshot using the
  existing `max_iterations` / goal-field pattern. The suppress is one-directional
  — the QuickMenu only mutes nudges for a session, never re-enables them against
  a global "off", so a global Settings change still flows through to the next
  new chat. `SessionFactory` emits the keys only when non-`nil`.
- **QuickMenu defaults re-seed from the built `SessionConfig`.** Bring-up and
  respawn recovery now seed `temporaryChat: !config.persist` and
  `memoryNudgesEnabled: config.memoryNudgeEnabled != false`, so a temporary
  chat shows the toggle ON for its lifetime and a suppressed-nudge session
  reflects its state. Per-session overrides cached in `quickMenuBySession`
  still win on switch.
- **Regression coverage expanded.** Python tests pin the structural-noise
  strip (including the `<html class="vector-toc-available">` nuke guard),
  citation/broken-table cleanup, the table-heavy fallback selection, and the
  nudge-suppress override. Swift tests pin the kwargs wire shape — `persist`
  defaults to `true`, `temporaryChat` flips it to `false`, and the nudge keys
  are omitted by default and emitted only when explicitly suppressed.
- **The distributable build defaults now target alpha.101 / build 101.**

## Distribution

- Published as monotonic Sparkle build 101.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

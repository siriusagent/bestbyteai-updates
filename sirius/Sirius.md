<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.115

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This is a reliability release for session reuse and first-party web research.
It fixes the closed Codex client failure reported on the Mac Studio, removes a
second worker-runtime resource leak found in the same sweep, and lets
`web_read` extract direct public PDF and Office documents instead of treating
them as empty HTML pages.

## Reliability fixes

- **New sessions no longer reuse a closed Codex client.** Closing a session or
  changing models no longer closes a provider owned by the worker cache. If an
  already-poisoned cache entry is encountered, Sirius discards and reconstructs
  it before the request. This fixes `Cannot send a request, as the client has
  been closed.` on a reused worker after a model hot-swap.
- **Multiple windows can safely share a worker provider.** A model change in
  one session no longer closes the provider still in use by another session,
  and background-handoff session close follows the same ownership rule.
- **Worker runtime rebinds clean up after themselves.** Replacing the service
  runtime closes the displaced CronHost, feedback-avoid drain, database, tool
  loader, memory, and provider resources instead of accumulating duplicate
  maintenance daemons.

## Web research

- **`web_read` now reads direct public PDF, DOCX, XLSX, and PPTX URLs.** It
  detects documents from response MIME metadata, `Content-Disposition`, URL
  suffixes, and PDF/OOXML signatures, then reuses Sirius's existing document
  conversion pipeline.
- **Suffixless PDF routes work.** Public's OTC risk disclosure and fee schedule
  now return extracted first-party Markdown even though neither URL ends in
  `.pdf`. Results include document kind, content type, extractor, optional PDF
  page count, warnings, and truncation metadata.
- **Document download stays bounded.** Sirius validates every redirect against
  its SSRF policy, enforces the shared 25 MiB attachment limit while streaming,
  rejects executable signatures, and uses the existing spill-file path for
  oversized Markdown results.

Direct public documents are supported in this slice. Sirius does not copy an
authenticated browser's cookies into the downloader or automatically follow a
document embedded inside an HTML wrapper.

## Notes

- **Sparkle build version** is `115` (`CFBundleVersion`), the primary comparison
  key for auto-update. Apps on `114` or earlier will offer this build.
- The signed core-runtime feed is refreshed as `0.1.0-alpha.115` so the app,
  appcast, and runtime component remain release-synchronized.

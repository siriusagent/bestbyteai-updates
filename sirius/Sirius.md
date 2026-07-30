<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.008

**Alpha channel release.** Sirius's core product surfaces and signed update
path are stable enough for regular use. The alpha label remains a pre-1.0
release channel — updates may still refine behavior and compatibility — but
this is a user release, not an installation or packaging test.

This release makes long-running agent work more resilient across context
compression and improves three practical automation paths: focusing native
editable controls, uploading local files through the Sirius browser, and
running shell commands that would otherwise disappear into a pager. It also
repairs another precise OpenAI-compatible sampling-error dialect.

## Session continuity

- **Automatic compression now recalls the active session before work
  continues.** When a turn compresses its live context, Sirius temporarily
  exposes only `session_search` and forces an exact read of the current
  session's recent transcript. Normal tools and system context return only
  after that read succeeds. A different session or page, an empty result, a
  text-only answer, or another tool keeps the gate closed, preventing the
  model from resuming with a plausible but stale reconstruction.

## Computer Use and Browser

- **Editable controls without a button-style primary action now focus
  semantically (BUG-382).** Native text fields and text areas that do not
  advertise `AXPress` use one `AXFocused = true` mutation and verify the exact
  element became focused. A failed focus reports directly instead of falling
  through to a coordinate click, while ordinary buttons and non-editable
  primary-less targets retain their established transports.

- **`browser_use_upload` can attach existing local files without opening
  Finder (BUG-383).** An agent can pass one absolute `path` or a `paths` array
  to a file input. Sirius validates up to 16 readable regular files and
  512 MiB combined, scopes the prepared selection to the exact tab and
  navigation, and completes WebKit's native chooser callback without exposing
  local paths to page JavaScript. Agent-driven clicks on file inputs fail
  closed with guidance to use the upload tool; manual clicks still open the
  native picker.

## Terminal and providers

- **Agent-issued shell commands no longer stall inside automatic pagers.**
  Sirius applies finite-output pager defaults to Git, `gh`, `man`, `psql`,
  `bat`, Delta, systemd clients, AWS CLI, and generic pager consumers across
  local, host-bridged, sandbox, credentialed, fallback, and detached
  execution. The policy is command-scoped: persistent CWD and unrelated
  exports survive, direct Terminal-panel input is unchanged, and an explicit
  command-local pager override still wins.

- **OpenAI-compatible sampling repair now understands explicit required-value
  errors (BUG-384).** A response such as
  `requires frequency_penalty=0` removes only that named request field and
  retries before the first streamed chunk, using the same model-local learned
  capability path as the existing “only 0 is supported” dialect. The fix is
  generic and does not depend on a provider or model-name exception.

## Notes

- **Sparkle build version** is `133` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `132` or earlier will offer
  this release.
- This release changes both the Swift host and the Python engine. The signed
  core-runtime feed is refreshed as `0.1.1-alpha.008` so the app, appcast, and
  Python runtime component remain release-synchronized.

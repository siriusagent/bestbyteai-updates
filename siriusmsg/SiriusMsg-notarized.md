<!-- sparkle-sign-warning:
IMPORTANT: This file is signed into the Sparkle appcast. Any modifications require re-running generate_appcast or sign_update before publishing.
-->
# SiriusMsg 0.0.1 (build 7)

Release update for the SDK pipeline, rich messaging parity work, and confirmed
outbound attachment delivery.

## Changed

- Added the generated Python and TypeScript SDK pipeline and tightened SDK
  subscription behavior so client contracts match the local protocol.
- Re-exported rich messaging models through `SiriusMsgKit` and added parity
  surfaces, recipe evidence, and validation smokes for rich-link/card flows.
- Refreshed the app's Home, Checks, Adapters, Chats, Advanced, and Recipes
  views around operational evidence, allowlists, adapter state, and release
  validation controls.

## Fixed

- Fixed outbound file sends through Messages by staging attachments into a
  Messages-readable user handoff location before ScriptingBridge dispatch.
- Prevented failed attachment rows from being counted as send confirmation by
  rejecting read-only Store matches with Messages delivery errors.
- Allowed Store confirmation for Messages-transcoded image sends when the
  delivered attachment keeps the requested display name and MIME type.
- Added sanitized outbound attachment row diagnostics for release validation
  without logging message bodies, raw handles, or full attachment paths.

## Verification

- App notarization: accepted by Apple notary service.
- DMG notarization: accepted by Apple notary service.
- Gatekeeper: accepted as Notarized Developer ID.
- DMG image verification: valid.
- Signed bundle verification: nested agent bundles `Python.framework`,
  `SiriusMsgHooks.framework`, and `SwiftPythonWorker` without Homebrew,
  user-home, checkout, private source, bytecode cache, or global
  `site-packages` linkage.
- Operational validation gate: passed with the notarized DMG path.
- Live signed-agent outbound file smoke: passed against a real PNG attachment,
  confirmed through read-only Messages Store evidence.

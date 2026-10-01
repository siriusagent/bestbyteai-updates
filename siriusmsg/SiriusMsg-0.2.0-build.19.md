<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# SiriusMsg 0.2.0 (build 19)

- Updated to SwiftPython SDK Preview 1.2, fixing cross-application worker ownership and preserving workers belonging to another live application. Update other applications using the shared SDK as well; older SDK writers retain their previous behavior.
- Fixed Codex connections installed through npm starting from Finder when Node is absent from the app's PATH. SiriusMsg resolves the installed native Codex engine for its managed server and proxy.
- Updated discovery for the current Codex desktop app layout and owner-validated socket links. Readiness requires a successful connection handshake; startup failures show more useful guidance.
- Show contact names in direct-chat and phone/email rows after Contacts permission is granted. Names refresh when Contacts changes or the app becomes active, and can be searched locally. Ambiguous matches keep the number or address; group titles are preserved.
- Preserve the selected person's name when adding a chat through the system Contacts picker. The picker remains available when general Contacts access is declined.
- Contact names stay in the app on this Mac and are not sent to agents.
- Keep long-lived connection readers and stalled control requests from occupying shared worker pools, preserving control deadlines and cancellation cleanup.

The signed app passed all seven alpha readiness checks on a real Mac after native bridge start and restart. The app and DMG are notarized and stapled.

This remains an alpha release. Recipient-visible typing dots remain unreliable and the Typing indicators control remains disabled. This release does not claim new live message-send or model-turn qualification. The stronger release-candidate messaging and recovery matrix remains unexecuted: Automation send, outbound file send, rich-link send, capability honesty, Messages restart, service restart, subscriber reconnect, and sleep/wake.

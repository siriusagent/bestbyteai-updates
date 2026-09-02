<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.033

Alpha.033 ships the complete runtime-component and credential-security work
completed after Alpha.032. It does not restore code from the withdrawn 0.1.2
line, and the separately documented Mobile Access work remains a plan rather
than a shipped feature.

## AutoFill now stays in stable browser chrome

- The floating `key.fill` control and its page-geometry tracking stream are
  gone. AutoFill now has one fixed toolbar position after Go.
- The only route in the build invokes WebKit's native context menu for the
  currently focused eligible field. macOS and the user's enabled AutoFill
  providers continue to own authentication, selection, and filling.
- Sirius receives no website username or password, never submits the form, and
  exposes no website-credential path to the agent, Python workers, logs, or
  persistence.

## Credentials & Access makes ownership explicit

- Settings now separates Agent & API Secrets, system-managed Website Sign-Ins,
  Passkeys & Security Keys, and Storage & Access.
- Sirius-owned secrets have declared namespaces and protection profiles for
  legacy automation, foreground/background automation, and explicit
  user-presence use.
- The signed app carries its team-scoped Data Protection Keychain access group;
  workers do not. Existing secrets remain compatible, and individual items can
  be upgraded explicitly without a bulk rewrite.
- Keychain replacement is add-or-update and loss-safe: a failed replacement no
  longer deletes the installed value first.

## Components can discover and install safe updates

- Components checks installed optional Python components with pip's own resolver
  inside Sirius's app-owned runtime and exact supported requirement ranges. It
  does not treat an unconstrained registry version as compatible.
- Available updates appear as explicit Update actions with accessible badges in
  the Settings action and Components category. Opening Settings does not clear
  them.
- Updates reuse isolated staging, complete import validation, and atomic
  promotion. Failure or cancellation leaves the current installation live.
- The embedded installer now supports the real script and `-c` child forms used
  by pip and PEP 517 source builds while preserving cancellation of the complete
  child process group.
- Signed schema-2 core-runtime metadata binds every runtime update to the exact
  compatible Sirius version and build before it becomes actionable.

## Reliability fixes

- BUG-496: removed the field-relative AutoFill overlay that could drift across
  the webpage.
- BUG-497: stopped Keychain saves from deleting an item before its replacement
  was accepted.
- BUG-498: fixed Credentials header sizing that could push Settings content out
  of the window.
- BUG-499: removed the LazyVStack/FlowLayout sizing loop that could hang the
  Credentials catalog.
- BUG-500: model discovery in Settings now uses the native main-interpreter
  Keychain bridge, so providers can read explicitly upgraded protected items.

## Verification

- Swift: 3,808 passed, 0 failed.
- Python: 7,999 passed with the non-slow gate, 0 failed.
- A freshly signed isolated Sirius app reached runtime-ready, passed the fixed
  WebKit AutoFill human gate, reported Data Protection Keychain availability,
  and completed protected-credential provider discovery.
- The release is not considered shipped until the exact Alpha.033 candidate
  passes Developer ID signing, the signed-bundle verifier including its sole
  Keychain access group, Apple notarization and stapling for both app and DMG,
  Gatekeeper, Sparkle/core-runtime signature verification, publication, and
  hosted-byte comparison.

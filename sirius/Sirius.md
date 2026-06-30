<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.96

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This is a **feature release** over alpha.95. It introduces **native computer
use** — Sirius can now observe and drive other macOS apps on your behalf, as a
sibling of the in-app Browser tab.

## Changes

- **Native computer use is available.** Sirius can take screenshots of other
  apps, read their on-screen elements, and act on them — click, type, scroll,
  set values, perform secondary actions, drag, and launch apps. The agent
  describes what it sees and chooses actions; the Swift host performs them on
  your real desktop.
- **Honest results.** When an app or surface genuinely can't be controlled in
  the background, Sirius says so instead of pretending it succeeded. Actions
  report whether their effect could be confirmed, so the agent can re-observe
  and recover rather than proceed on a false positive.
- **Safety and privacy floors.** Sensitive system surfaces (Keychain Access,
  the login window, authentication dialogs, and sensitive System Settings
  panes) are off-limits by default and never listed as targets. Password,
  verification, and payment fields are redacted from what the agent sees.
  Sirius itself is excluded from the target list unless you explicitly allow it.
  Screenshots are stored locally per session and cleaned up when the session
  ends.
- **You stay in control.** The first time Sirius drives an app each session,
  you approve it once — "Allow Sirius to control \<App\>?" — then it can act in
  that app, yield to you the moment you take over, never touch Keychain Access
  / the login window / auth dialogs / sensitive System Settings, and log every
  action. Revoke an app anytime from Permissions & Security. The whole
  capability can be disabled from Preferences, and there's a master "Allow
  Sirius to control other apps" toggle under Permissions & Security.
- **Optional focus recovery.** A new Preferences knob (Tools → Native Computer
  Use) lets Sirius briefly bring a target app forward when an action requires
  it, then restores your previous focus. It defaults to **off** so Sirius never
  steals focus unless you opt in.
- **Permissions required.** Computer use needs Accessibility and Screen
  Recording grants in System Settings → Privacy & Security. Sirius guides you
  to the right pane and reports a clear status when a grant is missing.
- **The bundled Python core runtime refreshes with this build.** The signed
  core-runtime feed ships the updated `sirius_agent` package, including the
  computer-use tools and provider.
- **The distributable build defaults now target alpha.96 / build 96.**

## Distribution

- Published as monotonic Sparkle build 96.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

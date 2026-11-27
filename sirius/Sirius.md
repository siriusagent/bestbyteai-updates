<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius 0.1.8.21

## Settings

- Test memory search in Context & Memory and compare it with a candidate search index before switching.
- Run upkeep from Maintenance & Storage and see which scheduled jobs failed. Choose a compatible conversation database to use after relaunch.
- Find tool controls and browser preferences together under Tools.

## Gemini and Goals

- Sirius keeps more of a long conversation eligible for Gemini’s cache when the clock, recalled memory, plan, or Goal state changes.
- Repeated tool calls that Sirius deliberately skips are recorded as skipped, so they no longer show up as interruptions.
- Fixed a case where a saved Goal stopped because Sirius mistook part of its action identifier for a credit-card number.

## Browser

- Keep typing in the composer while Sirius sends keys or pastes into the browser.

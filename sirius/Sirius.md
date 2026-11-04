<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius 0.1.6

## Clearer stops and more reliable cleanup

- Long-running turns now explain when their time budget has been reached, with
  guidance to inspect completed work before continuing unfinished actions.
- Separate notices distinguish a time-budget stop from stalled activity. Copy
  diagnostics includes timing and the latest completed action boundary.
- Terminal commands that exit the shell now remove their temporary scripts
  before reporting completion.
- Working outside a Git repository no longer produces noisy review-capture
  warnings. Actual capture failures remain available in diagnostics.
- Update and startup diagnostics remain available in Feedback after relaunch.

Requires macOS 26 or later on an Apple silicon Mac.

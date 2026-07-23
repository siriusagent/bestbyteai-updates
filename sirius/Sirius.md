<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.005

**Alpha channel release.** Sirius's core product surfaces and signed update
path are stable enough for regular use. The alpha label remains a pre-1.0
release channel — updates may still refine behavior and compatibility — but
this is a user release, not an installation or packaging test.

This is a same-day fix release for a Computer Use regression discovered
right after v0.1.1-alpha.004 shipped: replay safety could get stuck blocking
every mutation in a window after a single unconfirmed click.

## Fixed

- **Computer Use replay safety no longer blocks every mutation in a window
  after one unconfirmed click.** A live signed-app Chess session exposed
  this: an unconfirmed click on one square ("e2") correctly blocked an
  immediate replay of that same square, but then also blocked a click on a
  completely different square ("c1") after a fresh observation — effectively
  disabling Computer Use for the rest of the session. The fresh-observe
  escape hatch that should have proven the new target was distinct read the
  wrong tool-result field and compared a snapshot id without matching case,
  so it silently never fired. Both are fixed, with a regression test that
  reproduces the exact session shape.

## Notes

- **Sparkle build version** is `130` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `129` or earlier will offer
  this release.
- This release changes only Python engine code
  (`sirius_agent/engine/tool_cycles.py`); the signed core-runtime feed is
  refreshed as `0.1.1-alpha.005` to carry the fix.

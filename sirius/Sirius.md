<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.112

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

This release is a hotfix for session-worker tools that failed on non-ASCII text
when Sirius was launched from LaunchServices without a UTF-8 locale.

## What's new

- **Fixed grep/glob (and other tools) failing on non-ASCII text.** Session
  workers launched from the Dock/Finder often inherit no `LANG`/`LC_*`, so
  Python decoded subprocess output as ASCII. Searching Markdown with curly
  apostrophes (`Buyer’s`) or globbing paths with accented characters could
  raise `'ascii' codec can't decode byte…` and reject the tool. Workers now
  pin UTF-8 locale/I/O at spawn, and every first-party `subprocess text=True`
  call pins `encoding=utf-8` with replace-on-error.

## Notes

- **Sparkle build version** is `112` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on `111` or earlier will offer this
  build.
- Existing workers keep their inherited environment until app relaunch or
  worker respawn; install this build (or relaunch after update) to pick up
  the locale fix.

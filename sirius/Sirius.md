<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.011

**Alpha channel release.** Sirius's core product surfaces and signed update
path are stable enough for regular use. The alpha label remains a pre-1.0
release channel — updates may still refine behavior and compatibility — but
this is a user release, not an installation or packaging test.

This release makes website AutoFill behave like a native macOS field control
and makes post-compression recovery automatic and non-blocking.

## Native website AutoFill

- **The key attached to a focused form field now opens WebKit's real macOS
  AutoFill menu (BUG-394).** Sirius dispatches the field's native context menu
  and expands its AutoFill branch, leaving macOS and WebKit in control of the
  Contact…, Passwords…, and Credit Card… options. The launcher is a compact key
  and chevron with no bespoke credential picker, toolbar action, or background
  treatment.

## Post-compression reliability

- **Recovery no longer locks the agent behind a provider-authored tool call
  (BUG-391 follow-up).** Sirius hydrates a bounded recent-transcript snapshot
  directly into the next normal request. Normal tools and responses stay
  available immediately, and projection failures or later user turns cannot
  create a persistent retry gate.

## Notes

- **Sparkle build version** is `136` (`CFBundleVersion`), the primary
  comparison key for auto-update. Apps on build `135` or earlier will offer
  this release.
- This release changes both the Swift host and the Python engine. The signed
  core-runtime feed is refreshed as `0.1.1-alpha.011` so the app, appcast, and
  Python runtime component remain release-synchronized.

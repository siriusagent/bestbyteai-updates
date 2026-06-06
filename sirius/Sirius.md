<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.14

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Changes

- Fixes a crash when starting composer dictation on a Mac with no usable default
  audio input device. Sirius now validates the CoreAudio input formats before
  installing the audio tap and shows a non-fatal Sound Input settings message
  when macOS reports `0 ch`, `0 Hz` input.
- Keeps the dictation UI out of the listening state until the audio tap is
  installed and `AVAudioEngine` has started successfully.

## Distribution

- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, appcast, and signed core-runtime update feed are enabled
  for alpha update testing.

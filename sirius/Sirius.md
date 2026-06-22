<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.75

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Fixes

- **Browser no longer crashes while logging telemetry.** A diagnostic-logging
  path on the WebKit script-message delegate routed a main-actor closure through
  `Optional.map`, which tripped the Swift 6 executor-isolation check and
  segfaulted (`swift_task_isCurrentExecutorWithFlags`) on the `@objc` delegate
  thread. The path now avoids the isolation-crossing call, matching the
  `WebKitMainActorBridge` discipline. (BUG-268.)
- **Composer dictation cannot crash during audio setup.** Microphone capture now
  validates a default input device and usable input/tap formats before touching
  the `AVAudioEngine` input node or preparing the graph, turning a missing
  device or `0 ch` / `0 Hz` format into a recoverable "select an input device"
  status message instead of an `AVAudioIONodeImpl::AUI` / `AVAudioEngineGraph`
  crash. (BUG-267.)

## Changes

- **Composer dictation runs on Apple's macOS 26 `SpeechAnalyzer` stack.**
  Recognition now sits behind an internal backend seam with an honest, ordered
  fallback chain — `SpeechTranscriber` → `DictationTranscriber` →
  `SFSpeechRecognizer` (legacy floor) — chosen per session by locale and
  on-device model-asset availability. A natural speech pause finalizes a segment
  but no longer ends dictation; only the mic toggle, send, read-aloud, session
  switch, or cancel stops it. The composer mic UX, permissions, draft merge, and
  status-bar errors are unchanged.
- **Read aloud speaks SSML.** Assistant replies are spoken as SSML utterances
  (with XML escaping and paragraph cadence) and honor the system
  assistive-technology voice and speaking-rate settings, falling back to plain
  speech if SSML construction ever fails.

## Distribution

- Published as monotonic Sparkle build 75.
- Ships a refreshed signed core-runtime feed.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

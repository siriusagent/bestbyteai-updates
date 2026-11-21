<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius 0.1.8.12 · Build 235

## Terminal

- **Smooth live output and animations.** Sustained terminal output and full-screen TUIs hold a steady frame rate without stalling while completed history pages archive to disk or while the renderer flushes in-flight updates.
- **Stay responsive with long scrollback.** Large terminal histories no longer freeze the app on the main thread; command navigation resolves its target in the background instead of re-laying out the entire buffer.
- **Isolated host command runs.** Host commands run in their own PTY so your interactive shell and any typed input stay intact. If an alternate-screen program exits abruptly, Sirius restores the normal screen and cursor automatically and reports the real exit status.

## Providers and sign-in

- **Streamlined Google Gemini sign-in.** Connect Gemini with **Sign in with Google** or an API key. Sirius reserves a loopback port automatically for the bundled client, shows clearer browser-launch, consent, and retry states, and keeps an optional custom Google sign-in client available.
- **Better prompt caching on OpenRouter and Gemini.** With caching enabled, OpenRouter uses session-scoped routing affinity and configured Claude cache controls. Direct Gemini keeps stable tool guidance in the system instruction and honors a configured cached-content resource.

## Skills

- **Academic Paper Writer.** Added a bundled skill for drafting, revising, and auditing scientific manuscripts with notebook-generated figures, Mermaid workflow diagrams, consistency checks, and sidecar provenance tracking.

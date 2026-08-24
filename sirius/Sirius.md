<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.1-alpha.031

Alpha.031 restores Gemini tool-enabled chats and strengthens Sirius session,
Browser, and toolbar reliability.

## Gemini chats work with the full tool surface

- Gemini no longer receives an internally contradictory function declaration
  for `computer_use_press.expected_effect`.
- Structured schema members now select Gemini's compatible object or array
  type instead of leaving object-only `properties` attached to a string.
- The fix is provider-local: OpenAI-compatible, Anthropic, Codex, Ollama, and
  Ollama Cloud keep their native request contracts.
- A real `gemini-3.7-flash` request-shape regression now sends the built-in
  Computer Use schema through the streaming adapter and receives model text.

## Session and background-task reliability

- Durable background events no longer remain stranded behind a sinkless live
  session.
- Replacement sinks take ownership cleanly and replay unacknowledged events
  once per activation.
- Session-handle retirement closes Python-owned resources explicitly, while
  concurrent recovery remains single-flight and lifecycle-fenced.

## Browser maintainability without contract drift

- The Browser coordinator and page-automation implementation are split into
  focused authority, chrome, mutation, observation, state, and lifecycle
  files.
- Per-file behavior and policy tests guard the same Browser Use contracts while
  making future fixes smaller and easier to review.

## Toolbar control

- A new appearance preference can hide the Mind shortcut from the toolbar.
- The preference hot-applies across the app and does not remove access to the
  Mind surface itself.

## Verification

- Complete provider adapter gate: 561 passed, 1 intentional skip.
- Computer Use tool gate: 109 passed.
- Exact Gemini built-in schema request/stream regression passed.
- Generated wiki and whitespace audits passed.

Sirius Computer Use remains experimental. It takes a different route than
most computer use implementations: the Python agent plans through typed tools,
while the native Swift host owns macOS observation, input, authority, and
verification through SwiftPython worker callbacks.

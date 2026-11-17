<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius 0.1.8.1

- GPT-6.2 Sol and GPT-6.2 Astra appear in the model picker when your connected
  OpenAI account offers them.

## Update a local model server from Sirius

- If an Ollama model requires a newer server, Sirius shows the installed and
  required versions before the download. Open the vendor updater from the
  model, then check the server again to continue.
- Find update controls for Ollama and oMLX under Settings → Network &
  Providers → On This Mac. The oMLX load error also offers the update route.
- Ollama can reuse more of the previous prompt on follow-up messages. Sirius
  carries original message times and prior Ollama reasoning with the retained
  conversation.
- When the model keeps reading the same web pages and gets the same results,
  Sirius pauses the repeated reads and prompts it to reconsider its next step.

## Work with PDFs and browser sign-ins

- Mark up PDFs in Reader, then save or export the edited document.
- Sirius Security Key brings saved website logins and supported passkey flows
  into the built-in browser. Website sign-in can continue through a separate
  username and password page and pause for you to complete MFA.

Requires macOS 26 or later on an Apple silicon Mac.

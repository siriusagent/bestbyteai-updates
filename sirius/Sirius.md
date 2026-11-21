<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius 0.1.8.15 · Build 238

- **Update Ollama from Sirius.** On supported Ollama desktop versions, **Update and restart** now uses Ollama’s own shutdown mechanism so the server can stop and the new version can take over.
- **Clearer errors for incompatible GGUF files.** Sirius names the architecture Ollama couldn’t load and points you to the model’s Ollama Library package when one is available. For Inkling 2 Mini on Apple silicon, choose `inkling-2-mini:26b-a5b-nvfp4`.

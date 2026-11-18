<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius 0.1.8.5

- Upgrading Sirius and checking Components now revalidate the signed update feed, so a recently cached core runtime from the previous release cannot block startup.
- Choose a model for Codex, Claude Code, or Antigravity in Settings → Agent & Subagents. Open the agent and select **Change…** to search the models its CLI offers or use the account default.
- **Check for Updates** in Components now checks all three coding agents. **Manage in Sirius** creates a copy that Sirius can update. New tasks use the updated CLI, including tasks started in an existing chat. The original installation stays available to other apps.
- Core runtime appears first in Components. **Relaunch Sirius** is available directly on its row after installation.

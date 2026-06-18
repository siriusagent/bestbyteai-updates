<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# Sirius v0.1.0-alpha.71

**Strict pre-release unstable build.** This alpha exists for early installation,
packaging, and Sparkle update testing. It is not an RC, production release,
compatibility promise, or support boundary.

## Fixes

- **MCP OAuth works in noninteractive setup paths.** Streamable-HTTP MCP
  servers that require browser login now preserve the configured loopback
  redirect and report an actionable authorization state instead of failing
  probe/startup behind a generic transport error.
- **Backgrounded terminal prompts can receive input.** When Sirius
  auto-backgrounds a terminal command that is waiting for a prompt, the agent
  can now write stdin back into that same live process instead of restarting it
  and invalidating OAuth PKCE state.
- **Forced terminal stops hit the foreground command.** Non-control PTY signals
  now target the terminal's current foreground process group, improving forced
  cleanup for commands that are no longer in the shell's own process group.

## Distribution

- Published as monotonic Sparkle build 71.
- Ships a refreshed signed core-runtime feed for the MCP OAuth and terminal
  stdin fixes.
- Signed with Developer ID.
- Notarized and stapled.
- Sparkle public key, signed appcast, and signed core-runtime update feed are
  enabled for alpha update testing.

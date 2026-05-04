# OpenClaw Onboarding

Onboarding is the recommended way to set up OpenClaw. It configures the Gateway, channels, skills, and workspace in one guided flow.

## Run Onboarding

```bash
openclaw onboard
```

To reconfigure later:

```bash
openclaw configure
openclaw agents add <name>
```

## QuickStart vs Advanced

### QuickStart (defaults)

- Local gateway (loopback)
- Workspace default: `~/.openclaw/workspace`
- Gateway port: **18789**
- Gateway auth: **Token** (auto-generated)
- Tool policy: `coding` profile
- Tailscale exposure: **Off**

### Advanced (full control)

- Exposes every step (mode, workspace, gateway, channels, daemon, skills)
- Custom workspace location
- Custom port and bind address
- Detailed channel configuration

## What Onboarding Configures

### Local Mode (default)

1. **Model/Auth** — Choose provider (OpenAI, Anthropic, Google, Ollama, Custom), set API key or OAuth
2. **Workspace** — Location for agent files (default `~/.openclaw/workspace`)
3. **Gateway** — Port, bind address, auth mode, Tailscale exposure
4. **Channels** — Discord, Telegram, WhatsApp, Slack, Signal, iMessage, and more
5. **Daemon** — Install LaunchAgent (macOS), systemd user unit (Linux), or Scheduled Task (Windows)
6. **Health check** — Verify Gateway is running
7. **Skills** — Install recommended skills

### Remote Mode

Configures local client to connect to a remote Gateway. Does not install anything on the remote host.

## Non-Interactive Onboarding

```bash
# Full reset
openclaw onboard --reset

# Non-interactive mode
openclaw onboard --non-interactive --model anthropic --api-key sk-xxx
```

## Add Another Agent

```bash
openclaw agents add <name>
```

Creates a separate agent with its own workspace, sessions, and auth.

## Re-run Onboarding

Re-running onboarding does **not** wipe anything unless you explicitly choose **Reset**:

```bash
openclaw onboard --reset           # resets config, credentials, sessions
openclaw onboard --reset-scope full # includes workspace
```

## Verify Setup

```bash
openclaw dashboard        # Open Control UI
openclaw gateway status # Check Gateway is running
```

## Related

- [Overview](00-overview)
- [Installation](01-installation)
- [Gateway](03-gateway)
- [Channels](04-channels)
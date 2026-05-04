# OpenClaw Gateway

The Gateway is the central control plane for OpenClaw. It handles routing, channel connections, tools, and events.

## What the Gateway Does

The Gateway is a long-running Node.js service that:
- Routes messages between channels and AI agents
- Manages sessions and persistent memory
- Executes tools on behalf of the agent
- Provides HTTP/WebSocket APIs for the Control UI

## Start the Gateway

```bash
# Default port (18789)
openclaw gateway

# Custom port
openclaw gateway --port 3000

# Debug logging
openclaw gateway --verbose

# Force kill existing and start
openclaw gateway --force
```

## Gateway Status

```bash
openclaw gateway status
openclaw gateway status --deep    # includes system service scan
openclaw gateway status --json
```

Healthy output shows `Runtime: running`, `Connectivity probe: ok`.

## OpenAI-Compatible Endpoints

OpenClaw exposes OpenAI-compatible APIs on the Gateway port:

| Endpoint | Description |
|----------|-------------|
| `GET /v1/models` | List available models |
| `GET /v1/models/{id}` | Get model info |
| `POST /v1/embeddings` | Create embeddings |
| `POST /v1/chat/completions` | Chat completions |
| `POST /v1/responses` | Response API |

## Port and Bind Precedence

| Setting | Resolution Order |
|---------|------------------|
| Port | `--port` → `OPENCLAW_GATEWAY_PORT` → `gateway.port` → `18789` |
| Bind | CLI → `gateway.bind` → `loopback` |

## Hot Reload Modes

| Mode | Behavior |
|------|----------|
| `off` | No config reload |
| `hot` | Apply hot-safe changes only |
| `restart` | Restart on any change |
| `hybrid` (default) | Hot-apply when safe, restart when needed |

## Remote Access

### Tailscale (recommended)
Set up Tailscale for remote access to your Gateway.

### SSH Tunnel
```bash
ssh -N -L 18789:127.0.0.1:18789 user@host
```

Then connect to `ws://127.0.0.1:18789`.

## Service Management

### macOS (launchd)

```bash
openclaw gateway install
openclaw gateway restart
openclaw gateway stop
```

### Linux (systemd)

```bash
openclaw gateway install
systemctl --user enable --now openclaw-gateway
```

To persist after logout:
```bash
sudo loginctl enable-linger <user>
```

### Windows

```bash
openclaw gateway install
openclaw gateway restart
openclaw gateway stop
```

## Multiple Gateways

Run multiple gateways on the same host for isolation:

```bash
OPENCLAW_CONFIG_PATH=~/.openclaw/a.json \
OPENCLAW_STATE_DIR=~/.openclaw-a \
openclaw gateway --port 19001

OPENCLAW_CONFIG_PATH=~/.openclaw/b.json \
OPENCLAW_STATE_DIR=~/.openclaw-b \
openclaw gateway --port 19002
```

## Operator Commands

```bash
openclaw gateway status
openclaw gateway status --deep
openclaw gateway install
openclaw gateway restart
openclaw gateway stop
openclaw secrets reload
openclaw logs --follow
openclaw doctor
```

## Common Issues

| Issue | Solution |
|-------|----------|
| Port conflict | Use different port or `--force` |
| Auth required | Configure `gateway.auth.token` |
| Config reload | Use `openclaw secrets reload` |

## Related

- [Overview](00-overview.md)
- [Installation](01-installation.md)
- [Onboarding](02-onboarding.md)
- [Channels](04-channels.md)
- [Configuration](08-configuration.md)
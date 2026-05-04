# OpenClaw Configuration

OpenClaw is configured via `~/.openclaw/openclaw.json`. The config controls the Gateway, agents, tools, channels, plugins, and more.

## Config Location

- Default: `~/.openclaw/openclaw.json`
- Override: `OPENCLAW_CONFIG_PATH`
- State directory: `~/.openclaw/` (or `OPENCLAW_STATE_DIR`)

## Edit Config

```bash
openclaw configure                    # Interactive editor
openclaw config set <path> <value>    # Set a value
openclaw config get <path>           # Get a value
openclaw doctor                     # Diagnose and fix config issues
```

## Main Config Sections

```json
{
  "gateway": {
    "port": 18789,
    "bind": "loopback",
    "auth": {
      "mode": "token",
      "token": "your-token"
    }
  },
  "providers": { },
  "channels": { },
  "tools": { },
  "skills": { },
  "plugins": { },
  "agents": { }
}
```

## Gateway Config

| Setting | Description | Default |
|---------|-------------|---------|
| `gateway.port` | Gateway port | 18789 |
| `gateway.bind` | Bind mode (loopback/lan/0.0.0.0) | loopback |
| `gateway.auth.mode` | Auth mode (token/trusted-proxy/none) | token |
| `gateway.reload.mode` | Config reload (off/hot/restart/hybrid) | hybrid |

## Tools Config

```json
{
  "tools": {
    "profile": "coding",
    "allow": ["group:fs", "browser"],
    "deny": ["exec"]
  }
}
```

Tool profiles: `full`, `coding`, `messaging`, `minimal`

## Plugins Config

```json
{
  "plugins": {
    "enabled": true,
    "allow": ["voice-call"],
    "entries": {
      "voice-call": {
        "enabled": true,
        "config": { "provider": "twilio" }
      }
    }
  }
}
```

## Agents Config

```json
{
  "agents": {
    "defaults": {
      "model": "anthropic",
      "workspace": "~/.openclaw/workspace"
    },
    "list": [
      { "id": "main", "skills": ["github"] }
    ]
  }
}
```

## Environment Variables

| Variable | Description |
|----------|-------------|
| `OPENCLAW_HOME` | Home directory for path resolution |
| `OPENCLAW_CONFIG_PATH` | Override config file path |
| `OPENCLAW_STATE_DIR` | Override state directory |
| `OPENCLAW_GATEWAY_TOKEN` | Gateway auth token |
| `OPENCLAW_API_KEY` | Default API key |

## Verify Config

```bash
openclaw doctor         # Check for issues
openclaw doctor --fix  # Auto-fix issues
```

## Related

- [Overview](00-overview)
- [Gateway](03-gateway)
- [Tools](05-tools)
- [Skills](06-skills)
- [Plugins](07-plugins)
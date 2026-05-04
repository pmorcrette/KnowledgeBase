# OpenClaw Security

OpenClaw security assumes a personal assistant model—one trusted operator per gateway. It is not designed for hostile multi-tenant isolation.

## Security Model

- **One trusted operator** per gateway
- If multiple untrusted users share an agent, split trust boundaries (separate gateways, ideally separate hosts)
- Treat config/state modification as operator-level access

## Quick Security Audit

```bash
openclaw security audit
openclaw security audit --deep
openclaw security audit --fix
```

The audit checks:
- Inbound access (DM policies, allowlists)
- Tool blast radius (elevated tools + open rooms)
- Exec approval drift
- Network exposure (bind/auth)
- Browser control exposure
- Local disk permissions
- Plugin allowlists

## Hardened Baseline

This minimal config hardens an OpenClaw deployment:

```json
{
  "gateway": {
    "mode": "local",
    "bind": "loopback",
    "auth": { "mode": "token", "token": "replace-with-long-random-token" }
  },
  "session": {
    "dmScope": "per-channel-peer"
  },
  "tools": {
    "profile": "messaging",
    "deny": ["group:automation", "group:runtime", "group:fs", "sessions_spawn", "sessions_send"],
    "fs": { "workspaceOnly": true },
    "exec": { "security": "deny", "ask": "always" }
  }
}
```

## Access Control

### DM Policies

| Policy | Description |
|--------|-------------|
| `pairing` (default) | Unknown senders must approve via pairing code |
| `allowlist` | Only allowlisted users |
| `open` | Anyone can DM (requires `allowFrom: ["*"]`) |
| `disabled` | DMs disabled |

### Group Policies

- Use `groupPolicy: "allowlist"` + `groupAllowFrom` to restrict group triggers
- Use mention gating in groups: `requireMention: true`
- Avoid "always-on" bots in public rooms

## Tool Risk

Two built-in tools can make persistent changes:
- `gateway` — config inspection and modification
- `cron` — scheduled jobs

For agents handling untrusted content, deny these by default:

```json
{
  "tools": {
    "deny": ["gateway", "cron", "sessions_spawn", "sessions_send"]
  }
}
```

## Prompt Injection

Prompt injection manipulates the model into ignoring instructions. Mitigation:

- Keep DMs locked down (pairing/allowlists)
- Prefer mention gating in groups
- Run sensitive tools in sandbox
- Limit high-risk tools to trusted agents
- Use latest-generation models—older/smaller models are more susceptible
- Treat links, attachments, and external content as hostile

## Sandbox

Sandbox isolates tool execution:

```json
{
  "agents": {
    "defaults": {
      "sandbox": {
        "enabled": true,
        "docker": { }
      }
    }
  }
}
```

## File Permissions

Keep config and state private:

```bash
chmod 600 ~/.openclaw/openclaw.json
chmod 700 ~/.openclaw
```

## Network Exposure

- Default bind: `loopback` (local only)
- Prefer Tailscale Serve over LAN binds
- Never expose Gateway unauthenticated on `0.0.0.0`

## Gateway Auth

Required by default. Set a token:

```json
{
  "gateway": {
    "auth": { "mode": "token", "token": "your-token" }
  }
}
```

Generate one: `openclaw doctor --generate-gateway-token`

## Plugins Security

Plugins run in-process with the Gateway:
- Only install trusted plugins
- Use explicit `plugins.allow` lists
- Restart Gateway after changes

## Credential Storage

| Channel | Location |
|---------|----------|
| WhatsApp | `~/.openclaw/credentials/whatsapp/<accountId>/creds.json` |
| Telegram | config/env |
| Discord | config/env |
| Model auth | `~/.openclaw/agents/<agentId>/agent/auth-profiles.json` |

## Related

- [Overview](00-overview)
- [Gateway](03-gateway)
- [Channels](04-channels)
- [Configuration](08-configuration)
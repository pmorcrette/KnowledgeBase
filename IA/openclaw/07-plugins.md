# OpenClaw Plugins

Plugins extend OpenClaw's functionality by adding new capabilities through a structured interface.

## What Plugins Are

Plugins are installable modules that add new tools, channels, or integrations to OpenClaw.

## Plugin Types

| Type | Description |
|------|-------------|
| Tool plugins | Add new executable tools |
| Channel plugins | Add new messaging platforms |
| Storage plugins | Add new data storage backends |

## Installing Plugins

```bash
openclaw plugin install <name>
openclaw plugin list
openclaw plugin remove <name>
```

## Configuration

Plugins are configured in `openclaw.yaml` under the `plugins` section.
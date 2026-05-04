# OpenClaw Skills

Skills teach the agent when and how to use tools. Each skill is a directory with a `SKILL.md` file that provides context, constraints, and step-by-step guidance.

## What Skills Are

A skill is a markdown file (`SKILL.md`) injected into the system prompt. Skills give the agent context for doing specific tasks—like how to generate images, browse websites, or run code.

## Skill Locations

OpenClaw loads skills from, highest precedence first:

| Source | Path |
|--------|------|
| Workspace | `<workspace>/skills` |
| Project agent | `<workspace>/.agents/skills` |
| Personal agent | `~/.agents/skills` |
| Managed/local | `~/.openclaw/skills` |
| Bundled | shipped with install |
| Extra dirs | `skills.load.extraDirs` (config) |

Same name in multiple places → highest source wins.

## SKILL.md Format

```markdown
---
name: image-lab
description: Generate or edit images via a provider-backed image workflow
metadata:
  {"openclaw": {"requires": {"bins": ["uv"], "env": ["GEMINI_API_KEY"]}}
---
```

## Optional Frontmatter Keys

| Key | Description |
|-----|------------|
| `name` | Skill name |
| `description` | What the skill does |
| `user-invocable` | Expose as slash command (default: true) |
| `disable-model-invocation` | Keep instructions out of normal prompt |
| `command-dispatch` | Dispatch directly to a tool |
| `command-tool` | Tool name for dispatch |

## Gating (Load-time Filters)

Filter skills using `metadata.openclaw`:

```markdown
metadata:
  {
    "openclaw": {
      "requires": {
        "bins": ["curl"],
        "env": ["API_KEY"],
        "config": ["browser.enabled"]
      },
      "os": ["darwin", "linux"]
    }
  }
```

| Field | Description |
|-------|------------|
| `requires.bins` | Binaries that must exist on PATH |
| `requires.env` | Environment variables required |
| `requires.config` | Config paths that must be truthy |
| `os` | Platforms (darwin/linux/win32) |

## Per-Agent Allowlists

```json
{
  "agents": {
    "defaults": { "skills": ["github", "weather"] },
    "list": [
      { "id": "writer" },
      { "id": "docs", "skills": ["docs-search"] },
      { "id": "locked-down", "skills": [] }
    ]
  }
}
```

Agent allowlist rules:
- Omit `skills` to inherit defaults
- Empty array `[]` means no skills

## Install from ClawHub

```bash
openclaw skills install <skill-slug>
openclaw skills update --all
```

Browse skills at [https://clawhub.ai](https://clawhub.ai).

## Configuration

Configure skills in `~/.openclaw/openclaw.json`:

```json
{
  "skills": {
    "entries": {
      "image-lab": {
        "enabled": true,
        "env": { "GEMINI_API_KEY": "key-here" }
      },
      "peekaboo": { "enabled": false }
    }
  }
}
```

## Skills Watcher

OpenClaw watches skill folders and reloads on changes:

```json
{
  "skills": {
    "load": {
      "watch": true,
      "watchDebounceMs": 250
    }
  }
}
```

## Security

Treat third-party skills as untrusted code. Read them before enabling. Use sandboxed runs for risky tools.

## Related

- [Overview](00-overview.md)
- [Tools](05-tools.md)
- [Plugins](07-plugins.md)
- [Configuration](08-configuration.md)
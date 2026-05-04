# OpenClaw Tools

Tools are what the agent uses to take actions—running commands, browsing the web, reading files, sending messages, and more.

## Built-in Tools

These ship with OpenClaw and are available without plugins:

| Tool | What it does |
|------|--------------|
| `exec` / `process` | Run shell commands, manage background processes |
| `code_execution` | Run sandboxed remote Python analysis |
| `browser` | Control Chromium (navigate, click, screenshot) |
| `web_search` / `x_search` | Search the web, search X posts |
| `web_fetch` | Fetch page content |
| `read` / `write` / `edit` | File I/O in the workspace |
| `apply_patch` | Multi-hunk file patches |
| `message` | Send messages across all channels |
| `canvas` | Drive node Canvas |
| `nodes` | Discover and target paired devices |
| `cron` | Manage scheduled jobs |
| `gateway` | Inspect, patch, restart, or update Gateway |
| `image` | Analyze images |
| `image_generate` | Generate or edit images |
| `music_generate` | Generate music tracks |
| `video_generate` | Generate videos |
| `tts` | Text-to-speech conversion |
| `sessions_list` / `sessions_history` | Session management |
| `subagents` | Sub-agent orchestration |
| `session_status` | Lightweight status/readback |

## Tool Configuration

### Allow and Deny Lists

Control which tools the agent can call:

```json
{
  "tools": {
    "allow": ["group:fs", "browser", "web_search"],
    "deny": ["exec"]
  }
}
```

Deny always wins over allow.

### Tool Profiles

`tools.profile` sets a base allowlist:

| Profile | What it includes |
|---------|------------------|
| `full` | All core and optional plugin tools |
| `coding` | fs, runtime, web, sessions, memory, cron, image, music, video |
| `messaging` | messaging, sessions_list, sessions_history, sessions_send |
| `minimal` | session_status only |

### Tool Groups

Use `group:*` shorthands:

| Group | Tools |
|-------|-------|
| `group:runtime` | exec, process, code_execution |
| `group:fs` | read, write, edit, apply_patch |
| `group:sessions` | sessions_list, sessions_history, sessions_send, sessions_spawn |
| `group:memory` | memory_search, memory_get |
| `group:web` | web_search, x_search, web_fetch |
| `group:ui` | browser, canvas |
| `group:automation` | cron, gateway |
| `group:messaging` | message |
| `group:media` | image, image_generate, music_generate, video_generate, tts |

## Example Config

```json
{
  "tools": {
    "profile": "coding",
    "alsoAllow": ["browser"]
  }
}
```

## Related

- [Overview](00-overview.md)
- [Skills](06-skills.md)
- [Plugins](07-plugins.md)
- [Configuration](08-configuration.md)
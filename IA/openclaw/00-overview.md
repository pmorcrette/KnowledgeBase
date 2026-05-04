# OpenClaw Overview

OpenClaw is an open-source personal AI assistant that runs on your own devices. It connects AI models with your local files, messaging apps, and system capabilities to automate tasks around the clock.

## What OpenClaw Is

OpenClaw is a local-first AI agent runtime that acts as a proactive personal assistant. Unlike cloud AI services, OpenClaw runs on your infrastructure—your data stays on your machine. It works with your favorite chat apps (Discord, WhatsApp, Telegram, Slack, Signal, iMessage) and can execute real-world tasks through built-in tools.

The project started as Clawdbot, then Moltbot, and is now OpenClaw. Created by Peter Steinberger (PSPDFKit founder), it has grown to 68,000+ GitHub stars.

## Key Features

- **Local-First**: Runs on your machine—no data leaves your infrastructure
- **Multi-Channel**: Works with Discord, WhatsApp, Telegram, Slack, Signal, iMessage, Matrix, and more
- **Persistent Memory**: Remembers context across conversations
- **Built-in Tools**: Execute shell commands, control browsers, manage files, web search
- **Skills & Plugins**: Extend with community skills or build your own
- **Model Agnostic**: Works with OpenAI, Anthropic, Google, local models (Ollama)
- **Proactive Automation**: Cron jobs, reminders, background tasks

## Architecture

```
┌─────────────────────────────────────────────┐
│              OpenClaw Gateway              │
│  (Local control plane for sessions,       │
│   channels, tools, and events)             │
├─────────────────────────────────────────────┤
│  Channels    │  Tools   │  Plugins  │ Memory  │
│  Discord    │  exec   │  Custom  │ Long-  │
│  WhatsApp   │ browser │  Skills  │  term  │
│  Telegram   │ web_    │          │        │
│  Slack      │ search  │          │        │
└─────────────────────────────────────────────┘
```

## Quick Start

```bash
# Install OpenClaw
curl -fsSL https://openclaw.ai/install.sh | bash

# Run onboarding
openclaw onboard --install-daemon

# Check gateway status
openclaw gateway status
```

## File Structure

The OpenClaw data lives in:

- `~/.openclaw/` — Configuration and state
- `~/.openclaw/workspace/` — Agent workspace for file operations
- `~/.openclaw/config/` — Gateway configuration

## Related

- [Installation](01-installation)
- [Onboarding](02-onboarding)
- [Gateway](03-gateway)
- [Channels](04-channels)
- [Tools](05-tools)
- [Skills](06-skills)
- [Plugins](07-plugins)
- [Configuration](08-configuration)
- [Security](09-security)
# OpenClaw Installation

OpenClaw supports macOS, Linux, and Windows. The fastest way to install is using the installer script.

## System Requirements

- **Node 24** (recommended) or Node 22.14+
- **macOS, Linux, or Windows** (WSL2 recommended for Windows)
- `pnpm` only needed for source installs

## Recommended: Installer Script

### macOS / Linux / WSL2

```bash
curl -fsSL https://openclaw.ai/install.sh | bash
```

### Windows (PowerShell)

```powershell
iwr -useb https://openclaw.ai/install.ps1 | iex
```

### Install Without Onboarding

```bash
curl -fsSL https://openclaw.ai/install.sh | bash -s -- --no-onboard
```

## Alternative: npm / pnpm / bun

### npm

```bash
npm install -g openclaw@latest
openclaw onboard --install-daemon
```

### pnpm

```bash
pnpm add -g openclaw@latest
pnpm approve-builds -g
openclaw onboard --install-daemon
```

### bun

```bash
bun add -g openclaw@latest
openclaw onboard --install-daemon
```

## From Source

For contributors or development workflows:

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
pnpm install && pnpm build && pnpm ui:build
pnpm link --global
openclaw onboard --install-daemon
```

## Local Prefix Install

Install under `~/.openclaw` without system Node:

```bash
curl -fsSL https://openclaw.ai/install-cli.sh | bash
```

## Docker

```bash
docker run -d \
  --name openclaw \
  -v openclaw-data:/home/app/.openclaw \
  -e OPENCLAW_API_KEY=your-key \
  openclaw/openclaw
```

## Verify Installation

```bash
openclaw --version      # confirm CLI is available
openclaw doctor         # check for config issues
openclaw gateway status # verify Gateway is running
```

## Troubleshooting

### openclaw not found

Add global bin to PATH:

```bash
export PATH="$(npm prefix -g)/bin:$PATH"
```

Add to `~/.zshrc` or `~/.bashrc`.

### sharp build errors

```bash
SHARP_IGNORE_GLOBAL_LIBVIPS=1 npm install -g openclaw@latest
```

## Related

- [Overview](00-overview)
- [Onboarding](02-onboarding)
- [Updating](/install/updating)
- [Uninstall](/install/uninstall)
# POSIX Shell Overview

POSIX (Portable Operating System Interface) shell refers to the standardized Unix shell environment defined by IEEE POSIX.1-2017 (also known as IEEE 1003.1). The primary shell specified is the POSIX shell language, which forms the basis for the traditional Unix `sh` shell and is compatible with Bash, Dash, KornShell (ksh), and other POSIX-compliant shells.

## Shell Types

| Shell | Path | Description |
|-------|-----|-------------|
| sh | `/bin/sh` | Original Bourne shell |
| bash | `/bin/bash` | Bourne Again Shell |
| dash | `/bin/dash` | Debian Almquist Shell |
| ksh | `/bin/ksh` | KornShell |
| zsh | `/bin/zsh` | Z Shell |

The POSIX standard defines the `sh` language. On modern Linux systems:
- **Debian/Ubuntu**: `/bin/sh` → `dash`
- **RHEL/CentOS**: `/bin/sh` → `bash`
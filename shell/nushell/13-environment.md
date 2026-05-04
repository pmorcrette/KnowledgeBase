# Environment

Related: [I/O](12-io.md), [Modules](10-modules.md).

## Environment Variables

```nu
# Get
$env.PATH
$env.USER

# Set (scoped)
let-env FOO = "bar"

# Set in block (temporary)
with-env {FOO: "bar"} {
    print $env.FOO
}

# Update
let-env PATH = ($env.PATH | append "/new/path")
```

## Directory

```nu
# Change directory
cd /path

# Push/pop directory stack
cd /path
pushd /new/path
popd

# Current directory
$pwd

# Home directory
$HOME
```

## Configuration

```nu
# Config file location
$nu.config-path
$nu.env-path

# Default config directory
$nu.default-config-dir
```

## Environment File

```nu
# ~/.config/nushell/env.nu
$env.LANG = "en_US.UTF-8"
$env.EDITOR = "vim"

# Set path
let-env PATH = ($env.PATH | split row (char esep) | prepend "/home/user/bin" | str join (char esep))
```

## Config File

```nu
# ~/.config/nushell/config.nu
$env.config = {
    show_banner: false
}

# Keybindings
$env.keybindings = [
    {
        name: completion_menu
        modifier: none
        keycode: tab
        mode: [emacs vi_normal vi_insert]
        action: menu-next
    }
]
```

## Startup Files

| File | Purpose |
|------|---------|
| `env.nu` | Environment setup |
| `config.nu` | Configuration |
| `login.nu` | Login shell |
| `interactive.nu` | Interactive |
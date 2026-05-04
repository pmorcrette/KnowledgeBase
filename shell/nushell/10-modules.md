# Modules

Modules organize code into reusable units. Related: [Commands](09-commands), [Environment](13-environment).

## Creating Modules

```nu
# mymodule.nu
export def greet [name: string] {
    print $"Hello, ($name)!"
}

export const VERSION = "1.0.0"

export def add [a: int, b: int]: int -> int {
    $a + $b
}
```

## Importing Modules

```nu
# Import from file
use mymodule.nu

# Use commands
mymodule greet "world"

# Import specific
use mymodule.nu [greet, add]

# Import with alias
use mymodule.nu as mu
mu greet "world"
```

## Module Syntax

```nu
# Inline module
module mymodule {
    def greeting []: string -> string {
        "Hello"
    }
}
```

## Use Command

```nu
# Use all exports
use mymodule

# Use with prefix
use mymodule --prefix mu
mu greeting

# Import environment
use mymodule.nu --env
```

## Submodules

```nu
# module.nu
module inner {
    export def inner_cmd [] { }
}

export def outer_cmd [] { }
export module inner
```
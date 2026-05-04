# Functions

Reusable code blocks. Use [Variables](01-variables) and can use [Arithmetic](09-arithmetic).

## Function Definition

```sh
# POSIX way
name() {
    # local variables
    local arg1="$1"
    local result
    
    # function body
    echo "$arg1"
}

# Using return for exit status only
name() {
    return 0  # success
    return 1  # failure
}

# Get function output via command substitution
result=$(name "argument")
```
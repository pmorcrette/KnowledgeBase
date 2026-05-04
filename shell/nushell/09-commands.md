# Custom Commands

Custom commands are first-class commands in Nushell. Related: [Modules](10-modules), [Control Flow](08-control-flow).

## Basic Command

```nu
def greet [name: string] {
    print $"Hello, ($name)!"
}

greet "world"
```

## Return Value

Commands implicitly return the last expression:

```nu
def double [x: int] {
    $x * 2
}

let result = double 21
print $result  # 42
```

## Parameters

```nu
# Optional parameter
def greet [name?: string] {
    print $"Hello, ($name ?? "World")!"
}

# Default value
def greet [name: string = "World"] {
    print $"Hello, ($name)!"
}

# Multiple params
def add [a: int, b: int] {
    $a + $b
}

# Rest parameters
def sum [...nums: int] {
    $nums | math sum
}
sum 1 2 3 4  # 10

# Flags (named parameters)
def greeting [--formal: bool, --name: string] {
    if $formal {
        print $"Good day, ($name)"
    } else {
        print $"Hi, ($name)"
    }
}
greeting --formal --name "Alice"
```

## Pipeline Input/Output

```nu
# Accept pipeline input
def incr []: int -> int {
    $in + 1
}

5 | incr  # 6

# Explicit signature
def process []: [string, int] -> [string, int] {
    [$in.0, ($in.1 + 1)]
}
```

## Closures

```nu
# Closure parameter
let apply = {|x| $x * 2}
apply 21

# Built-in commands with closures
[1 2 3] | where $it > 1
[1 2 3] | each {|x| $x * 2}
[1 2 3] | reduce {|acc, it| $acc + $it}
```
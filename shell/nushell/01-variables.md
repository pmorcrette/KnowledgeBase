# Variables

Nushell uses `$` prefix for variables. Variables are immutable by default. Related: [Types](02-types.md), [Operators](03-operators.md).

## Variable Declaration

```nu
# Immutable variable (let)
let name = "world"

# Mutable variable (mut)
mut count = 0
$count = $count + 1

# Constant (evaluated at parse-time)
const CONFIG_DIR = ($env.HOME | path join ".config")
```

## Variable Types

```nu
# Type annotations
let count: int = 42
let name: string = "nushell"
let items: list<string> = ["a", "b", "c"]
let record: record = {name: "test", value: 1}

# Any type
let anything: any = "string or number"
```

## Assignment Operators (mutable)

| Operator | Description |
|----------|-------------|
| `=` | Assign new value |
| `+=` | Add and assign |
| `-=` | Subtract and assign |
| `*=` | Multiply and assign |
| `/=` | Divide and assign |
| `++=` | Append to list |

```nu
mut list = [1, 2]
$list ++= 3
print $list  # [1, 2, 3]
```

## Variable Names

Cannot contain: space, caret, dash, equals, plus, at, question, asterisk, slash, backslash, period, or colon (at start).
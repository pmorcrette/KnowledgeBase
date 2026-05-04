# Data Types

Nushell is a statically typed language with several built-in types. Related: [Variables](01-variables), [Strings](04-strings), [Lists](05-lists).

## Basic Types

| Type | Description | Example |
|------|-------------|---------|
| `int` | Integer | `42` |
| `float` | Decimal | `3.14` |
| `string` | Text | `"hello"` |
| `bool` | Boolean | `$true` / `$false` |
| `nothing` | Null | `null` |

## Compound Types

```nu
# List
let list: list<int> = [1, 2, 3]

# Record (object)
let record = {name: "test", age: 30}

# Table
let table = [[name age]; [bob 25] [alice 30]]

# Closure
let closure = { || print "hi" }
```

## Range

```nu
1..5        # 1, 2, 3, 4, 5
1..<5       # 1, 2, 3, 4 (exclusive end)
```

## Filesize and Duration

```nu
1kb      # 1024 bytes
1mb      # 1048576 bytes
1sec     # 1 second
1min     # 60 seconds
```

## Type Conversion

```nu
# Convert to int
"42" | into int

# Convert to string
42 | into string

# Convert to table (from CSV)
"a,b\n1,2" | from csv
```
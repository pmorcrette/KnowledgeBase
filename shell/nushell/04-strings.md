# Strings

String manipulation in Nushell. Related: [Types](02-types), [Regex](15-regex).

## String Creation

```nu
# Basic string
let s = "hello"

# String interpolation
let name = "world"
print $"Hello ($name)"

# String with expression
print $"(1 + 2) = (1 + 2)"

# Raw string (r"...")
let path = r"C:\Users\name"
```

## String Commands

```nu
# Split
"a,b,c" | split column ","

# Join
["a", "b", "c"] | str join ","

# Contains
"hello" | str contains "ll"

# Starts/Ends with
"hello" | str starts-with "he"
"hello" | str ends-with "lo"

# Case conversion
"Hello" | str down-case
"HELLO" | str up-case

# Replace
"hello world" | str replace "world" "nu"
```

## Parsing

```nu
# Parse to record
"key=value" | parse "{key}={value}"

# Parse CSV
"a,b\n1,2" | from csv

# Parse JSON
'{"a": 1}' | from json
```

## String Slicing

```nu
# Get character at index
"hello" | get index 1  # "e"

# Slice
"hello" | str slice 1..3  # "el"
```
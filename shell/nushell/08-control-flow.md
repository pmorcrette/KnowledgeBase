# Control Flow

Related: [Operators](03-operators.md), [Commands](09-commands.md).

## If/Else

```nu
if $condition {
    print "yes"
} else if $other {
    print "maybe"
} else {
    print "no"
}

# One-liner
if $x > 0 { "positive" } else { "non-positive" }
```

## Match

```nu
let value = 2

match $value {
    1 => "one"
    2 => "two"
    _ => "other"
}

# Type matching
match ($val | describe) {
    "int" => "integer"
    "string" => "string"
    _ => "other"
}
```

## Loops

```nu
# For loop
for $item in $items {
    print $item
}

# For with index
for $item in ($items | enumerate) {
    print $"($item.index): ($item.item)"
}

# Range
for $x in 1..5 {
    print $x
}

# While
let mut count = 0
while $count < 5 {
    print $count
    $count = $count + 1
}

# Loop (infinite loop)
loop {
    # break or return to exit
}
```

## Try/Catch

```nu
try {
    "invalid" | into int
} catch {
    print $"Error: ($in)"
}

# With default value
let result = try { "x" | into int } catch { 0 }
```
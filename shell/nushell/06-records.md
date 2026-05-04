# Records

Records are key-value collections like JSON objects. Related: [Types](02-types), [Tables](07-tables).

## Record Creation

```nu
let person = {
    name: "Alice"
    age: 30
}

# Or with types
let person: record<name: string, age: int> = {
    name: "Alice"
    age: 30
}
```

## Record Access

```nu
# Get field
$person.name

# Use cell-path
$person | get age

# Update field
$person | update age 31

# Add field
$person | insert email "alice@test.com"

# Merge records
$person | merge {age: 31, city: "NYC"}
```

## Spread Operator

```nu
let defaults = {a: 1, b: 2}
let override = {b: 3, c: 4}

# Spread - later values override
{...$defaults, ...$override}  # {a: 1, b: 3, c: 4}
```

## Convert to/from

```nu
# Record to table (transpose)
{name: "test", age: 30} | transpose key value

# Table to record (first row)
[[name age]; [bob 25]] | to record
# Tables

Tables are structured data with columns and rows. Related: [Records](06-records.md), [Lists](05-lists.md), [Pipelines](11-pipelines.md).

## Table Creation

```nu
let data = [
    [name age city];
    [Alice 30 NYC]
    [Bob 25 LA]
    [Carol 35 Chicago]
]

# Empty with types
let empty: table<name: string, age: int> = []
```

## Table Operations

```nu
# Select columns
$data | select name

# Reject columns
$data | reject age

# Filter rows
$data | where age > 30

# Sort

$data | sort-by age
$data | sort-by age -r  # reverse

# Group
$data | group-by city

# Rename
$data | rename old_name new_name
```

## Table Transforms

```nu
# Insert computed column
$data | insert full_name { |row| $"($row.name) ($row.age)" }

# Update with expression
$data | update age { |age| $age + 1 }

# Merge columns
$data | merge {age_plus: {$it.age + 1}}
```

## Aggregate

```nu
# Summary stats
$data | summary

# Math operations
[1 2 3] | math sum
[1 2 3] | math avg
[1 2 3] | math min
[1 2 3] | math max

# Booleans
[$true $false $true] | math and  # false
[$true $false $true] | math or   # true
```
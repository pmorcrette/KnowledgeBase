# Lists

Lists are ordered, indexable collections. Related: [Types](02-types), [Tables](07-tables), [Pipelines](11-pipelines).

## List Creation

```nu
let fruits = ["apple", "banana", "orange"]

# Typeannotated
let nums: list<int> = [1, 2, 3]
```

## List Operations

```nu
# Get by index
$fruits.0          # "apple"
$fruits | get 0     # same

# Get length
$fruits | length    # 3

# First/Last
$fruits | first
$fruits | last

# Append
$fruits | append "grape"

# Prepend
$fruits | prepend "mango"

# Update
$fruits | update 0 "avocado"

# Insert at index
$fruits | insert 1 "kiwi"

# Delete at index
$fruits | drop nth 1
```

## List Iteration

```nu
# Iteratee with index
for $item in (['a' 'b'] | enumerate) {
    print $"($item.index) = ($item.item)"
}

# Each
[1 2 3] | each { |x| $x * 2 }

# Par-each (parallel)
[1 2 3] | par-each { |x| $x * 2 }

# Reduce
[1 2 3] | reduce { |it, acc| $acc + $it.item }
```

## List Filtering

```nu
# Where
[1 2 3 4 5] | where $it > 2

# Take
[1 2 3 4 5] | take 3

# Skip
[1 2 3 4 5] | skip 2

# Range slice
[1 2 3 4 5] | 1..3
```
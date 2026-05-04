# Pipelines

Nushell's core design - data flows through commands. Related to [Lists](05-lists.md), [Tables](07-tables.md), [Commands](14-commands.md).

## Pipeline Basics

```nu
ls | sort-by size | reverse | first 5

# Same as
(ls | sort-by size | reverse | first 5)
```

## Pipeline Input ($in)

```nu
# $in holds previous output
echo 5 | do { $in * 2 }  # 10
```

## Multiple Pipeline Stages

```nu
# Sort then take
$items | sort | take 5

# Filter then map
[1 2 3 4 5] | where $it > 2 | each {|x| $x * 2}
# [6, 8, 10]
```

## Stream vs Collected

```nu
# Streaming (lazily evaluated)
[1 2 3] | each {|x| print $x }

# Collect first
[1 2 3] | each {|x| $x } | to json
```

## Commands by Category

### Filters

- `where` - Filter by condition
- `select` - Select columns
- `get` - Get column/value
- `update` - Update values
- `insert` - Insert columns
- `reject` - Remove columns
- `first` / `last` - First/last N
- `take` / `skip` - Take/skip N
- `each` - Iterate
- `reduce` - Aggregate

### Error Handling

Related: [Errors](16-errors.md).

### Generators

- `seq` - Generate sequence
- `generate` - Lazy generation

### Sorts

- `sort-by` - Sort by column
- `uniq` - Remove duplicates
- `group-by` - Group by value

### Statistics

- `summary` - Statistics
- `math` - Math operations
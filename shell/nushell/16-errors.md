# Errors and Debugging

Related: [Control Flow](08-control-flow.md), [Pipelines](11-pipelines.md).

## Try/Catch

```nu
try {
    "invalid" | into int
} catch {
    print $"Error: ($in)"
}

# With default
let num = try { "x" | into int } catch { 0 }
```

## Error Info

```nu
# Get error message
try { error make {msg: "failed"} } catch { $in.msg }

# Error code
try { error make {msg: "failed", code: (make error code: {val: 1}) } }
```

## Debug Commands

```nu
# Inspect value
inspect

# Print value
print $var
dbg $var   # debug print with type

# Time commands
timeit { command }
```

## Type Inspection

```nu
# Get type
$val | describe
$val | type-of

# Check type
if ($val | describe) == "int" { }
```

## Profiling

```nu
# Basic timing
^time nu -c 'ls | length'

# Benchmark
use std benchmark
benchmark { ls }
```

## Help System

```nu
# Command help
help <command>

# Search commands
help --find <term>

# All commands
help commands

# Explore command
help <command> | explore
```
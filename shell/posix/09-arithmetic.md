# Arithmetic

Mathematical operations. Used in [Loops](07-loops.md) and [Functions](08-functions.md).

## Arithmetic Expansion

```sh
# Basic arithmetic
result=$((1 + 2))
result=$((10 - 5))
result=$((3 * 4))
result=$((10 / 3))      # Integer division
result=$((10 % 3))      # Modulo

# Increment/decrement
((count++))
((--count))

# Comparison (0 = true, 1 = false)
((5 > 3))    # true
```

## expr Command

```sh
# Legacy arithmetic
result=$(expr 2 + 3)
result=$(expr 10 / 3)
```
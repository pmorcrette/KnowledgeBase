# Conditional Expressions

Control flow with test conditions. See also: [Case Statement](06-case.md), [Loops](07-loops.md).

## Test Command

```sh
# File tests
[ -f file ]      # Regular file exists
[ -d dir ]        # Directory exists
[ -r file ]      # Readable
[ -w file ]      # Writable
[ -x file ]      # Executable
[ -s file ]      # Non-empty file
[ -L file ]      # Symbolic link

# String tests
[ -z "$str" ]    # Empty string
[ -n "$str" ]    # Non-empty string
[ "$a" = "$b" ]  # Equal
[ "$a" != "$b" ] # Not equal

# Numeric tests
[ "$a" -eq "$b" ] # Equal
[ "$a" -ne "$b" ] # Not equal
[ "$a" -lt "$b" ] # Less than
[ "$a" -le "$b" ] # Less or equal
[ "$a" -gt "$b" ] # Greater than
[ "$a" -ge "$b" ] # Greater or equal
```

## Conditional Blocks

```sh
if [ condition ]; then
    # commands
elif [ condition ]; then
    # commands
else
    # commands
fi

# One-line form
[ -f file ] && echo "exists"
```
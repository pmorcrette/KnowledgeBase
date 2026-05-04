# Quoting

Quoting controls how the shell interprets special characters. Essential for working with [Variables](01-variables.md) and [String Operations](11-strings.md).

## Types of Quoting

```sh
# Double quotes - allows variable expansion
echo "Current user: $USER"

# Single quotes - literal interpretation
echo 'Current user: $USER'
# Output: Current user: $USER

# Backslash - escaping individual characters
echo "Path: \$PATH"
```
# I/O Redirection

Redirection controls input/output file descriptors. Works with [Pipes](04-pipes) and is essential for [Utilities](13-utilities).

## File Descriptors

| FD | Name | Description |
|----|------|-------------|
| 0 | stdin | Standard input |
| 1 | stdout | Standard output |
| 2 | stderr | Standard error |

## Redirection Operators

```sh
# Redirect stdout to file (overwrite)
command > output.txt

# Redirect stdout to file (append)
command >> output.txt

# Redirect stderr
command 2> errors.txt

# Redirect both stdout and stderr
command &> all.txt
command > all.txt 2>&1
command > all.txt 2>&1  # Note: order matters

# Redirect stdin from file
command < input.txt

# Here-doc
cat << EOF
Multi-line
text content
EOF

# Here-string
command <<< "string input"
```
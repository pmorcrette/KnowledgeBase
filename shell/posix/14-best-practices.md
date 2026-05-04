# Scripting Best Practices

Guidelines for writing robust shell scripts. Includes uses of: [Variables](01-variables), [Functions](08-functions), [Case Statements](06-case), [Arithmetic](09-arithmetic).

## Shebang

```sh
#!/bin/sh
# Use /bin/sh for maximum portability
# Avoidbashisms for strict POSIX compliance
```

## Error Handling

```sh
# Exit on error
set -e

# Exit on undefined variable
set -u

# Exit on pipe failure
set -o pipefail

# Combine options
set -euo pipefail
```

## Debugging

```sh
# Dry run
set -n  # check syntax without executing

# xtrace - print commands
set -x
```

## Common Patterns

### Option Parsing

```sh
while getopts "abc:" opt; do
    case $opt in
        a) flag_a=1 ;;
        b) flag_b=1 ;;
        c) value_c="$OPTARG" ;;
        :) echo "Option -$OPTARG requires argument" ;;
        \?) echo "Invalid option" ;;
    esac
done
shift $((OPTIND - 1))
```

### Temporary Files

```sh
# Create temp file
tmp=$(mktemp)
trap 'rm -f "$tmp"' EXIT
```

### Lock Files

```sh
# Simple locking
lockfile=/tmp/script.lock
if ! mkdir "$lockfile" 2>/dev/null; then
    echo "Already running"
    exit 1
fi
trap 'rmdir "$lockfile"' EXIT
```
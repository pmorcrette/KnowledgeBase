# Variables and Parameters

Variable assignment and parameter expansion are fundamental to POSIX shell scripting. See also: [Quoting](02-quoting), [Functions](08-functions), [Arithmetic](09-arithmetic).

## Variable Assignment

``` sh
# Simple assignment (no spaces around =)
name="value"
number=42

# Read-only variable
readonly CONST="immutable"

# Export variable to environment
export PATH="$PATH:/usr/local/bin"
```

## Parameter Expansion

| Syntax                 | Description                   |
| ---------------------- | ----------------------------- |
| `${var}`               | Value of var                  |
| `${var:-default}`      | Default if var unset or empty |
| `${var:=default}`      | Assign default if unset       |
| `${var:?error}`        | Error if unset                |
| `${var:+alternate}`    | Alternate if set              |
| `${#var}`              | Length of var                 |
| `${var:offset:length}` | Substring                     |


## Special Parameters

| Parameter    | Description                       |
| ------------ | --------------------------------- |
| `$0`         | Script name                       |
| `$1` to `$9` | Positional arguments              |
| `$#`         | Number of arguments               |
| `$*`         | All arguments (as one word)       |
| `$@`         | All arguments (as separate words) |
| `$?`         | Exit status of last command       |
| `$$`         | Current process ID                |
| `$!`         | PID of last background job        |
| `$-`         | Current flags                     |


# Globbing

Pattern matching for filenames. Works with [Loops](07-loops) and relates to [Case Statement](06-case).

## Pattern Matching

| Pattern | Description |
|--------|-------------|
| `*` | Any string |
| `?` | Any single character |
| `[abc]` | Any character in set |
| `[!abc]` | Not in set |
| `?(pattern)` | Zero or one |
| `*(pattern)` | Zero or more |
| `+(pattern)` | One or more |
| `@(pattern)` | Exactly one |
| `@(pattern1\|pattern2)` | One of |

## Extended Globbing (bash)

```sh
# Files with specific extension
ls *.txt

# Hidden and regular files
ls .* *

# Range
ls file[0-9].txt
```
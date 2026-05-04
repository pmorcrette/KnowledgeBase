# String Operations

Text manipulation. Works with [Variables](01-variables) (parameter expansion) and [Quoting](02-quoting).

## Parameter Expansion for Strings

```sh
# Remove matching prefix
${var#pattern}   # shortest match
${var##pattern}  # longest match

# Remove matching suffix
${var%pattern}   # shortest match
${var%%pattern}  # longest match

# Replace patterns
${var/pattern/replacement}   # first match
${var//pattern/replacement}  # all matches

# Case conversion (bash 4+)
${var,,}  # lowercase
${var^^}  # uppercase
```

## sed Stream Editor

```sh
# Replace text
sed 's/old/new/' file

# Replace globally
sed 's/old/new/g'

# In-place edit
sed -i 's/old/new/g' file

# Multiple commands
sed -e 's/a/b/' -e 's/c/d/' file

# Delete lines
sed '/pattern/d' file
```
# Arrays (Bash/ksh Extension)

Array operations. Bash extension building on [Variables](01-variables). Related: [Loops](07-loops), [String Operations](11-strings).

## Array Operations

```sh
# Declare array
arr=(one two three)

# Access elements
echo "${arr[0]}"   # first element
echo "${arr[@]}"   # all elements
echo "${#arr[@]}"  # array length

# Append elements
arr+=("four")

# Slice
echo "${arr[@]:1:2}"  # elements 1 and 2
```
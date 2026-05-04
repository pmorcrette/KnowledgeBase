# Loops

Iteration constructs. Works with [Conditional Expressions](05-conditionals) and uses [Case Statements](06-case).

## For Loop

```sh
# Iterate over items
for item in list1 list2 list3; do
    echo "$item"
done

# C-style for loop
for ((i=0; i<10; i++)); do
    echo "$i"
done

# Iterate over files
for file in *.txt; do
    echo "$file"
done

# Iterate over directory
for item in /path/*; do
    echo "$item"
done
```

## While Loop

```sh
# Read lines from file
while read -r line; do
    echo "$line"
done < input.txt

# Command substitution
while read -r line; do
    echo "$line"
done < <(command)

# Countdown
count=5
while [ $count -gt 0 ]; do
    echo "$count"
    count=$((count - 1))
done
```

## Until Loop

```sh
until [ condition ]; do
    commands
done
```
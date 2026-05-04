# Common Utilities

Essential command-line tools. Many use [Redirection](03-redirection) and [Pipes](04-pipes).

## echo and printf

```sh
# echo with escape sequences
echo -e "Line1\nLine2"
echo -n "No newline"

# printf (more reliable)
printf "Value: %s\n" "$value"
printf "%05d\n" 42
printf "%.2f\n" 3.14159
```

## read

```sh
# Read single line
read -r line

# Read with prompt
read -p "Enter value: " line

# Silent input (passwords)
read -sp "Password: " pass

# Read into array
read -ra arr <<< "a b c"

# Timeout
read -t 5 -r line
```

## sort and uniq

```sh
# Sort lines
sort file
sort -u file     # unique lines

# Numeric sort
sort -n file

# Reverse sort
sort -r file

# Remove duplicates
uniq file
uniq -c file    # count occurrences
```

## find

```sh
# Find files
find . -name "*.txt"
find . -type f
find . -type d
find . -mtime +7    # modified > 7 days ago

# Execute commands
find . -name "*.txt" -exec cat {} \;
find . -name "*.txt" -exec rm {} \;
find . -name "*.txt" -delete
```

## grep

```sh
# Basic search
grep "pattern" file
grep -r "pattern" .

# Options
grep -i "pattern"   # case insensitive
grep -v "pattern"   # invert match
grep -w "pattern"   # word match
grep -n "pattern"   # show line numbers
grep -c "pattern"   # count
grep -l "pattern"   # list filenames
```
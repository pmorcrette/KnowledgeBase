# Regex and Patterns

Related: [Strings](04-strings), [Control Flow](08-control-flow).

## Regex Matching

```nu
# Contains
"hello" =~ "el"     # true

# Does not contain
"hello" !~ "xx"    # true

# Match
"abc123" =~ /\d+/    # true
```

## Parsing with Regex

```nu
# Parse with capture
"name=Alice, age=30" | parse "(?P<name>\w+), age=(?P<age>\d+)"

# From capture
{name: "Alice", age: "30"} | get name
```

## Find and Replace

```nu
# Replace first
"hello" | str replace --find "l" "L"

# Replace all
"hello" | str replace "l" "L"

# Regex replace
"hello world" | parse '(\w+) (\w+)'
```

## Glob Patterns

```nu
# Standard
ls *.txt
glob **/*.rs

# Question mark for single char
glob file?.txt
```

## String Match

```nu
# Contains substring
"hello" | str contains "ll"

# Starts with
"hello" | str starts-with "hel"

# Ends with
"hello" | str ends-with "lo"

# Matches regex
"hello" | str matches 'h.*o'
```
# Operators

Nushell supports various operators for comparison, arithmetic, and more. Related to [Types](02-types.md), [Control Flow](08-control-flow.md).

## Arithmetic Operators

| Operator | Description |
|----------|-------------|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `//` | Floor Division |
| `**` | Exponentiation |
| `%` | Modulo |

## Comparison Operators

| Operator | Description |
|----------|-------------|
| `==` | Equal |
| `!=` | Not Equal |
| `<` | Less Than |
| `<=` | Less or Equal |
| `>` | Greater Than |
| `>=` | Greater or Equal |

## Boolean Operators

| Operator | Description |
|----------|-------------|
| `and` | Logical AND |
| `or` | Logical OR |
| `not` | Logical NOT |
| `^^` | Exclusive OR |

## Regex Operators

```nu
"hello" =~ "ll"     # true - contains
"hello" !~ "xx"     # true - does not contain
```

## Range Operators

```nu
5 in 1..10          # true
5 not in 1..5       # true (exclusive)
```
# Nushell Overview

Nushell (Nu) is a modern shell written in Rust that treats everything as structured data. It combines the power of a programming language with a shell interface, offering structured inputs/outputs instead of plain text.

## Key Differences from POSIX Shells

- **Structured Data**: Commands return tables, not plain text
- **Static Typing**: Support for type annotations
- **Immutability**: Variables are immutable by default
- **Pipeline-First**: Every command works with pipelines

## Installation

```sh
# Linux/macOS
cargo install nushell

# or via package manager
brew install nushell

# Windows
winget install nushell.nushell
```

## Basic Syntax

```nu
# Echo returns a value (not printed by default)
echo "hello"

# Print to stdout
print "hello"

# Variables use $ prefix
let name = "world"
print $"($name)"

# Commands return values that are rendered
ls
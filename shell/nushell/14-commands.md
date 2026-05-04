# Built-in Commands

Common Nushell commands organized by category. Related: [Pipelines](11-pipelines.md), [I/O](12-io.md).

## File System

```nu
ls              # List directory
cd              # Change directory
pwd             # Print working directory
mkdir           # Make directory
rm              # Remove file
cp              # Copy
mv              # Move
touch           # Create empty file
open            # Open/read file
save            # Save to file
glob            # Glob pattern
```

## Data Processing

```nu
from json       # Parse JSON
from csv       # Parse CSV
to json        # To JSON
to csv         # To CSV
select         # Select columns
get            # Get value
where          # Filter rows
sort-by        # Sort
group-by       # Group by
reduce         # Aggregate
each           # Iterate
par-each       # Parallel each
```

## Text

```nu
echo           # Create value
print          # Print to stdout
str            # String operations
lines          # Split into lines
split          # Split string
parse          # Parse string
format         # Format strings
```

## Conversion

```nu
into           # Convert type
into int       # To integer
into string    # To string
into bool     # To boolean
into binary   # To binary
```

## Network

```nu
http get       # GET request
http head     # HEAD request
http post     # POST request
http put      # PUT request
http delete   # DELETE request
curl          # HTTP client
```

## System

```nu
ps             # Processes
date           # Date/time
sys            # System info
cache          # Cache operations
help           # Help system
version        # Nushell version
```
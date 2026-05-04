# Pipes and Command Sequences

Pipes connect commands together. Works with [Redirection](03-redirection) and builds on [Conditionals](05-conditionals) for error handling.

## Pipeline

```sh
# Pipe output to next command
cmd1 | cmd2 | cmd3

# Command sequences
cmd1 && cmd2  # cmd2 runs if cmd1 succeeds
cmd1 || cmd2  # cmd2 runs if cmd1 fails
cmd1 ; cmd2   # cmd2 runs after cmd1
```
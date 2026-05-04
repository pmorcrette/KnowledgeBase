# Portable Shell Programming

Writing portable POSIX scripts. Related: [Best Practices](14-best-practices.md), [Resources](16-resources.md) (ShellCheck).

## Check for POSIX Compliance

```sh
# Use shellcheck for linting
shellcheck -s sh script.sh

# Check with bashisms detection
shellcheck -s sh -o all script.sh
```

## Common Non-POSIX Bashisms to Avoid

- `[[ ]]` compound command (use `[ ]`)
- `function` keyword (use `name()`)
- `local` outside function (not portable)
- `$RANDOM` (bash extension)
- `source` (use `.`)
- `==` in `[ ]` (use `=`)
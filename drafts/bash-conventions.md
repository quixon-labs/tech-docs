# Bash Conventions

## Must

- MUST use `set -Eeuo pipefail` right after hash-bang declaration.
- MUST use snake casing for function names, and don't use hyphen.
- MUST use `[[` .. `]]` for test and don't use `[` or `test` command.
    - POSIX compatible test syntax has many unintuitive nuances that make life difficult.

## Do

- DO start scripts with `#/bin/bash`. 
    - It's concise and every system we target has bash in `/bin`. So there's no need to use env.
- DO split long lines with `\`.
- DO write a function called `run` and/or `main` when your script spans more than a single line or two.
  - Use `main` for args validation/usage and run for actual execution if required.

## Don't

- DONT use semi-colons unless needed. 
    - The syntax is noisy enough already.

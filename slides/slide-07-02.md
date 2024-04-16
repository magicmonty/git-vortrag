# Conventional Commits

```commit
<type>[optional scope]: <short description>

[optional body]

[optional footer(s)]
```

- type: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `chore`
- scope in braces: `(<scope>)`
  - i.e. `feat(parser): add ability to parse arrays`
- footer: `BREAKING CHANGE`, `Closes`, `Fixes`, `Refs`

## Example:

```commit
fix(backend): prevent racing of requests

Introduce a request id and a reference to latest request. Dismiss
incoming responses other than from latest request.

Remove timeouts which were used to mitigate the racing issue but are
obsolete now.

Refs: #123
```

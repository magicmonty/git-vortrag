# Identifying Commits

Identify by `HEAD`, branch, tag, commit hash

## Relative references

- Alternative writings

  ```text
    ┌─────┐    ┌─────┐    ┌────┐    ┌───┐
    │ X~3 │ ←─ │ X~2 │ ←─ │ X~ │ ←─ │ X │
    └─────┘    └─────┘    └────┘    └───┘
      X~~~       X~~        X^
      X~2                   X^1
                            X~1
  ```

- Used in combinations:
  - `HEAD^` - the parent of the current commit
  - `HEAD~3` - the third commit before the current commit
  - `main^2` - the second parent of the main branch
  - `2c3d4f^` - the parent of the commit with the hash `2c3d4f`

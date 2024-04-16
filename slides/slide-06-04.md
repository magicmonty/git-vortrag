# Identifying Commits

Identify by `HEAD`, branch, tag, commit hash

## Relative references

- `~` and `^` can be combined

  ```text
                         ┌─────┐
                         │ X^3 │ ←─────┐
                         └─────┘       │
             ┌──────┐    ┌─────┐       │
             │ X^2~ │ ←─ │ X^2 │ ←───┐ │
             └──────┘    └─────┘     │ │
    ┌─────┐    ┌─────┐    ┌────┐    ┌───┐
    │ X~3 │ ←─ │ X~2 │ ←─ │ X~ │ ←─ │ X │
    └─────┘    └─────┘    └────┘    └───┘
  ```

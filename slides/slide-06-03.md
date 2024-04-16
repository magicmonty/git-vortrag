# Identifying Commits

Identify by `HEAD`, branch, tag, commit hash

## Relative references

- `~` --> going back in history

  ```text
    ┌─────┐    ┌─────┐    ┌────┐    ┌───┐
    │ X~3 │ ←─ │ X~2 │ ←─ │ X~ │ ←─ │ X │
    └─────┘    └─────┘    └────┘    └───┘
  ```

- `^` --> parent of a commit

  ```text
                         ┌─────┐
                         │ X^3 │ ←─────┐
                         └─────┘       │
                         ┌─────┐       │
                         │ X^2 │ ←───┐ │
                         └─────┘     │ │
    ┌─────┐    ┌─────┐    ┌────┐    ┌───┐
    │ X~3 │ ←─ │ X~2 │ ←─ │ X~ │ ←─ │ X │
    └─────┘    └─────┘    └────┘    └───┘
  ```

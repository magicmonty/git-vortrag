# Rebase

- Rewrites history
- **Never** do on shared branches

```bash
git rebase main
```

```text
            main
  ┌───┐    ┌───┐    ┌────┐    ┌────┐
  │ A │ ←─ │ B │ ←─ │ C' │ ←─ │ D' │
  └───┘    └───┘    └────┘    └────┘
                           feature (HEAD)
```

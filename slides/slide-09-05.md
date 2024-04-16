# Rebase

- Rewrites history
- **Never** do on shared branches

```bash
git checkout main
```

```text
         main (HEAD)
  ┌───┐    ┌───┐    ┌────┐    ┌────┐
  │ A │ ←─ │ B │ ←─ │ C' │ ←─ │ D' │
  └───┘    └───┘    └────┘    └────┘
                             feature
```

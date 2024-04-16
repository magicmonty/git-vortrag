# Rebase

- Rewrites history
- **Never** do on shared branches

```bash
git branch -d feature
```

```text
                            main (HEAD)
  ┌───┐    ┌───┐    ┌────┐    ┌────┐
  │ A │ ←─ │ B │ ←─ │ C' │ ←─ │ D' │
  └───┘    └───┘    └────┘    └────┘
```

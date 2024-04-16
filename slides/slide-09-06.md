# Rebase

- Rewrites history
- **Never** do on shared branches

```bash
git merge --ff-only feature
```

```text
                            main (HEAD)
  ┌───┐    ┌───┐    ┌────┐    ┌────┐
  │ A │ ←─ │ B │ ←─ │ C' │ ←─ │ D' │
  └───┘    └───┘    └────┘    └────┘
                             feature
```

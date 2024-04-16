# Merge

```bash
git merge feature
```

```text
                          main (HEAD)
  ┌───┐    ┌───┐             ┌───┐
  │ A │ ←─ │ B │ ←────────── │ E │
  └───┘    └───┘             └───┘
    ↑                          │
    │      ┌───┐    ┌───┐      │
    └───── │ C │ ←─ │ D │ ←────┘
           └───┘    └───┘
                   feature
```

# Fast forward Merge

```bash
git merge main
```

```text
            main
  ┌───┐    ┌───┐
  │ A │ ←─ │ B │ ←─────────────┐
  └───┘    └───┘               │
    ↑                          │
    │      ┌───┐    ┌───┐    ┌───┐
    └───── │ C │ ←─ │ D │ ←─ │ E │
           └───┘    └───┘    └───┘
                          feature (HEAD)
```

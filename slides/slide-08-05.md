# Fast forward Merge

```bash
git checkout main
```

```text
         main (HEAD)
  ┌───┐    ┌───┐
  │ A │ ←─ │ B │ ←─────────────┐
  └───┘    └───┘               │
    ↑                          │
    │      ┌───┐    ┌───┐    ┌───┐
    └───── │ C │ ←─ │ D │ ←─ │ E │
           └───┘    └───┘    └───┘
                            feature
```

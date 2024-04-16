# Fast forward Merge

```bash
git merge --ff-only feature
```

 
```text
  ┌───┐    ┌───┐
  │ A │ ←─ │ B │ ←─────────────┐
  └───┘    └───┘               │
    ↑                      main (HEAD)
    │      ┌───┐    ┌───┐    ┌───┐
    └───── │ C │ ←─ │ D │ ←─ │ E │
           └───┘    └───┘    └───┘
                            feature
```

# Interactive Rebase

- for reordering, squashing, rewording commits
- rewrites history
- **Never** do on shared branches

```bash
git rebase -i main
# Mark commit C as "pick" and commit D as "squash"
```

```text
            main
  ┌───┐    ┌───┐    ┌────┐
  │ A │ ←─ │ B │ ←─ │ CD │
  └───┘    └───┘    └────┘
                 feature (HEAD)
```

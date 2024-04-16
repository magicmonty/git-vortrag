# Configure git

- Set user name and email

  ```bash
  git config --global user.name "John Doe"
  git config --global user.email "john.doe@bayoo.net"
  ```

- Set default branch name to `main`

  ```bash
  git config --global init.defaultBranch main
  ```

- Set default editor

  ```bash
  git config --global core.editor "nvim"
  ```

- fetch/pull behavior

  ```bash
  git config --global pull.rebase true
  git config --global pull.ff only
  git config --global fetch.prune true
  ```

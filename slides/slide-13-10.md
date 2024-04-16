# Configure git

- diff and merge tools

  - [Beyond Compare](https://www.scootersoftware.com/)
  - [Git Delta](https://github.com/dandavison/delta)

  ```bash
  git config --globel delta.features "side-by-side line-numbers decorations"
  git config --global delta.whitespace-error-style "22 reverse"
  git config --global 'delta "decorations"'.commit-decoration-style "bold yellow box ul"
  git config --global 'delta "decorations"'.file-decoration-style "none"
  git config --global 'delta "decorations"'.file-style "bold yellow ul"
  git.config --global interactive.diffFilter "delta --color-only"
  ```

- rerere (Reuse Recorded Resolution)

  ```bash
  git config --global rerere.enabled true
  git config --global rerere.autoupdate true
  ```

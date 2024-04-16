# Configure git

- Commit message handling in editor

  ```bash
  git config --global commit.cleanup scissors
  ```

- Aliases

  ```bash
  git config --global alias.a 'add'
  ```

## Useful aliases

- a = `add`
- aa = `add --all`
- amend = `commit --amend --no-edit`
- reword = `commit --amend --message`
- ci = `commit`
- cim = `commit --message`
- cima = `commit --all --message`
- cleanf = `clean -xdf`
- co = `checkout`
- dt = `difftool`
- mt = `mergetool`
- l = `log --oneline --max-count=15`
- gl = `log --graph --oneline --decorate --branches --all`
- st = `status`

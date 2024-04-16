# Git 101

## Git Basics

### Initialize a git repository

- create a new repository

  ```bash
  # Create a new directory
  $ mkdir <directory>

  # go into the directory
  $ cd <directory>

  # Initialize the git repository
  $ git init
  Leeres Git-Repository in <directory>/.git/ initialisiert

  # Create an initial file. Good candidates are README.md, .gitignore
  $ echo "# Git Test" >> README.md

  $ git status
  Auf Branch main

  Noch keine Commits

  Unversionierte Dateien:
    (benutzen Sie "git add <Datei>...", um die Änderungen zum Commit vorzumerken)
          README.md

  nichts zum Commit vorgemerkt, aber es gibt unversionierte Dateien
  (benutzen Sie "git add" zum Versionieren)

  $ git add README.md

  $ git status
  Auf Branch main

  Noch keine Commits

  Zum Commit vorgemerkte Änderungen:
    (benutzen Sie "git rm --cached <Datei>..." zum Entfernen aus der Staging-Area)
          neue Datei:     README.md

  $ git commit -m "Initial commit"
  [main (Root-Commit) a84ef55] Initial commit
   1 file changed, 1 insertion(+)
   create mode 100644 README.md

  $ git status
  Auf Branch main
  nichts zu committen, Arbeitsverzeichnis unverändert
  ```

- clone an existing repository

  ```bash
  git clone <url> [<directory>]
  ```

  - **Pro Tip**:
    Setup SSH keys to avoid entering your password
    every time you push to a remote repository.

### Working with git

#### Basic workflow

- change files
- Add files to the staging area

  ```bash
  git add <file>
  ```

- Check the Status of the repository

  ```bash
  git status
  ```

- Commit changes

  ```bash
  git commit -m "<commit message>"
  ```

### Working with remote repositories

### Push changes to a remote repository

- initial push

  ```bash
    git push -u <remote> <branch>
  ```

  - `-u` sets up tracking information for the branch, so git remembers the remote to push to

- for each subsequent push a `git push` is sufficient

### Pull changes from a remote repository

### Branches/Tags

- Create a new branch
- Switch to a branch
- Delete a branch
- Difference between branches and tags

### Undo changes

- Unstage changes
- Discard changes
- Revert changes
- Reset changes
- Amend changes

### Identifying Commits

- HEAD, branch, tag, commit hash
- Relative references

  - `~` going back in history

    ```text
      ┌─────┐    ┌─────┐    ┌────┐    ┌───┐
      │ X~3 │ ←─ │ X~2 │ ←─ │ X~ │ ←─ │ X │
      └─────┘    └─────┘    └────┘    └───┘
    ```

  - `^` parent of a commit

    ```text
                           ┌─────┐
                           │ X^3 │ ←─────┐
                           └─────┘       │
                           ┌─────┐       │
                           │ X^2 │ ←───┐ │
                           └─────┘     │ │
      ┌─────┐    ┌─────┐    ┌────┐    ┌───┐
      │ X~3 │ ←─ │ X~2 │ ←─ │ X~ │ ←─ │ X │
      └─────┘    └─────┘    └────┘    └───┘
    ```

  - `~` and `^` can be combined

    ```text
                           ┌─────┐
                           │ X^3 │ ←─────┐
                           └─────┘       │
               ┌──────┐    ┌─────┐       │
               │ X^2~ │ ←─ │ X^2 │ ←───┐ │
               └──────┘    └─────┘     │ │
      ┌─────┐    ┌─────┐    ┌────┐    ┌───┐
      │ X~3 │ ←─ │ X~2 │ ←─ │ X~ │ ←─ │ X │
      └─────┘    └─────┘    └────┘    └───┘
    ```

  - Alternative writings

    ```text
      ┌─────┐    ┌─────┐    ┌────┐    ┌───┐
      │ X~3 │ ←─ │ X~2 │ ←─ │ X~ │ ←─ │ X │
      └─────┘    └─────┘    └────┘    └───┘
        X~~~       X~~        X^
        X~2                   X^1
                              X~1
    ```

  - Used in combinations:
    - `HEAD^` - the parent of the current commit
    - `HEAD~3` - the third commit before the current commit
    - `main^2` - the second parent of the main branch
    - `2c3d4f^` - the parent of the commit with the hash `2c3d4f`

## Advanced Git

### Better commit messages

- [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)
- [better-commits](https://github.com/Everduin94/better-commits)

  ```bash
  npm install -g better-commits
  ```

### Stash changes

```bash
git stash
git stash list
git stash apply
git stash pop
git stash drop
```

### Merge / Rebase

##### Merge

```text
         main (HEAD)
  ┌───┐    ┌───┐
  │ A │ ←─ │ B │
  └───┘    └───┘
    ↑
    │      ┌───┐    ┌───┐
    └───── │ C │ ←─ │ D │
           └───┘    └───┘
                   feature
```

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

##### Fast forward

```text
            main
  ┌───┐    ┌───┐
  │ A │ ←─ │ B │
  └───┘    └───┘
    ↑
    │      ┌───┐    ┌───┐
    └───── │ C │ ←─ │ D │
           └───┘    └───┘
                 feature (HEAD)
```

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

##### Rebase

- Rewrites history
- **Never** do on shared branches

```text
            main
  ┌───┐    ┌───┐
  │ A │ ←─ │ B │
  └───┘    └───┘
    ↑
    │      ┌───┐    ┌───┐
    └───── │ C │ ←─ │ D │
           └───┘    └───┘
                 feature (HEAD)
```

```bash
git rebase main
```

```text
            main
  ┌───┐    ┌───┐    ┌────┐    ┌────┐
  │ A │ ←─ │ B │ ←─ │ C' │ ←─ │ D' │
  └───┘    └───┘    └────┘    └────┘
                           feature (HEAD)
```

```bash
git checkout main
```

```text
         main (HEAD)
  ┌───┐    ┌───┐    ┌────┐    ┌────┐
  │ A │ ←─ │ B │ ←─ │ C' │ ←─ │ D' │
  └───┘    └───┘    └────┘    └────┘
                             feature
```

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

```bash
git branch -d feature
```

```text
                            main (HEAD)
  ┌───┐    ┌───┐    ┌────┐    ┌────┐
  │ A │ ←─ │ B │ ←─ │ C' │ ←─ │ D' │
  └───┘    └───┘    └────┘    └────┘
```

#### Interactive rebase

- for reordering, squashing, rewording commits
- rewrite history
- **Never** do on shared branches

```text
            main
  ┌───┐    ┌───┐
  │ A │ ←─ │ B │
  └───┘    └───┘
    ↑
    │      ┌───┐    ┌───┐
    └───── │ C │ ←─ │ D │
           └───┘    └───┘
                 feature (HEAD)
```

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

- Cherry-pick commits
- Rebase branches
- Amend commits
- Merge conflicts

### Configure git

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

- Commit message handling in editor

  ```bash
  git config --global commit.cleanup scissors
  ```

- useful aliases

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

  ```bash
  $ mkdir test
  $ cd test
  $ git init
  $ echo "Hello World" > test.txt
  $ git add test.txt
  $ git commit -m "Initial commit"
  $ git checkout -b feature
  $ echo "Hello mundo" > test.txt
  $ git add test.txt
  $ git commit -m "Change hello world to hello mundo"
  $ git checkout main
  $ echo "Hola world" > test.txt
  $ git add test.txt
  $ git commit -m "Change hello world to hola world"
  $ git merge feature
  Auto-merging test.txt
  CONFLICT (content): Merge conflict in test.txt
  Recorded preimage for 'test.txt'
  Automatic merge failed; fix conflicts and then commit the result.

  $ git mergetool
  $ git add test.txt
  $ git commit --no-edit
  Recorded resolution for 'test.txt'.
  [main b323e72] Merge branch 'feature'

  $ git reset --hard HEAD^
  $ git checkout feature

  $ git rebase main
  Auto-merging test.txt
  CONFLICT (content): Merge conflict in test.txt
  error: could not apply f199ade... mundo
  hint: Resolve all conflicts manually, mark them as resolved with
  hint: "git add/rm <conflicted_files>", then run "git rebase --continue".
  hint: You can instead skip this commit: run "git rebase --skip".
  hint: To abort and get back to the state before "git rebase", run "git rebase --abort".
  Staged 'test.txt' using previous resolution.
  Could not apply f199ade... mundo
  ```

### Use git hooks

- husky

### Use git worktree

### Use git bisect

- see [Git Bisect example](https://github.com/EvanLovely/git-bisect-example)

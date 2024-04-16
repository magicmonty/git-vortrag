# Working with Remote Repositories

## Push changes to a remote

- initial push

  ```bash
    git push -u <remote> <branch>
  ```

  - `-u` sets up tracking information for the branch, so git remembers the remote to push to

- for each subsequent push a `git push` is sufficient
- if you have forgotten the `-u` option, you can set the tracking information later:

  ```bash
    git branch --set-upstream-to=<remote>/<branch>
  ```
